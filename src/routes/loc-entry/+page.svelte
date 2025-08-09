<script lang="ts">
	function parseFile(content: string) {
		const lines = content.split('\n');
		const result: GroupEntry[] = [];
		let currentGroup: GroupEntry | undefined;
		let i = 0;

		while (i < lines.length) {
			const line = lines[i];

			// Skip empty lines
			if (!line) {
				i++;
				continue;
			}

			// Group comment: // string at start of line (no tab)
			if (line.indexOf('// ') === 0) {
				result.push({
					group: line.substring(3).trim(),
					trans: []
				});

				currentGroup = result.at(-1);
				i++;
				continue;
			}

			// Subgroup comment: tab + //
			if (line.indexOf('\t// ') === 0) {
				if (currentGroup) {
					if (currentGroup.subgroup) {
						// Create new subgroup
						result.push({
							group: currentGroup.group,
							subgroup: line.substring(4).trim(),
							trans: []
						});

						currentGroup = result.at(-1);
					} else {
						currentGroup.subgroup = line.substring(4).trim();
					}
				}

				i++;
				continue;
			}

			// loc-entry: simple entry
			if (line.startsWith('loc-entry:')) {
				let fullContent = line.substring(10).trim();

				// Handle multiline entries
				let j = i + 1;
				while (
					j < lines.length &&
					!lines[j].trim().startsWith('loc-') &&
					!lines[j].trim().startsWith('//')
				) {
					if (lines[j].trim()) {
						fullContent += ' ' + lines[j].trim();
					}
					j++;
				}

				const match = fullContent.match(/"([^"]*)"[\s]*"([^"]*)"/);
				if (match && currentGroup) {
					currentGroup.trans.push({
						eng: match[1],
						ru: match[2]
					});
				}

				i = j;
				continue;
			}

			// loc-case: complex entry with male/female
			if (line.startsWith('loc-case:')) {
				let fullContent = line.substring(9).trim();

				// Collect all lines until next loc- or // directive
				let j = i + 1;
				while (
					j < lines.length &&
					!lines[j].trim().startsWith('loc-') &&
					!lines[j].trim().startsWith('//')
				) {
					if (lines[j].trim()) {
						fullContent += ' ' + lines[j].trim();
					}
					j++;
				}

				// Parse: "string1" male: "string2" female: "string3"
				const caseMatch = fullContent.match(
					/"([^"]*)"[\s]*male:[\s]*"([^"]*)"[\s]*female:[\s]*"([^"]*)"/
				);

				if (caseMatch && currentGroup) {
					currentGroup.trans.push({
						eng: caseMatch[1],
						ru: {
							male: caseMatch[2],
							female: caseMatch[3]
						}
					});
				}

				i = j;
				continue;
			}

			i++;
		}

		return result;
	}

	function dataToFileContent(parsedData: GroupEntry[]) {
		let content = '';
		let currentGroup = '';

		for (const groupEntry of parsedData) {
			if (currentGroup !== groupEntry.group) {
				content += '// ' + groupEntry.group + '\n';
				currentGroup = groupEntry.group;
			}

			if (groupEntry.subgroup) {
				content += '\t// ' + groupEntry.subgroup + '\n';
			}

			content += groupEntry.trans
				.map((entry) => {
					if (typeof entry.ru === 'string') {
						return `loc-entry: "${entry.eng}" "${entry.ru}"`;
					} else {
						return `loc-case: "${entry.eng}"\n\tmale: "${entry.ru.male}"\n\tfemale: "${entry.ru.female}"\n`;
					}
				})
				.join('\n');

			content += '\n\n';
		}

		return content;
	}

	function handleFileExport() {
		const blob = new Blob([dataToFileContent(parsedData)], {
			type: 'text/plain'
		});

		const url = URL.createObjectURL(blob);
		const a = document.createElement('a');
		a.href = url;
		a.download = loadedFilename;
		document.body.appendChild(a);
		a.click();
		document.body.removeChild(a);
		URL.revokeObjectURL(url);
	}

	type GroupEntry = {
		group: string;
		subgroup?: string;
		trans: {
			eng: string;
			ru:
				| string
				| {
						male: string;
						female: string;
				  };
		}[];
	};

	let parsedData: GroupEntry[] = $state([]);
	let loadedFilename = $state('');

	function isGenderedEntry(ru: string | { male: string; female: string }) {
		return typeof ru === 'object';
	}

	function changeEntryType(groupIndex: number, transIndex: number) {
		const entryRu = parsedData[groupIndex].trans[transIndex].ru;
		if (entryRu) {
			if (isGenderedEntry(entryRu)) {
				parsedData[groupIndex].trans[transIndex].ru = entryRu.male;
			} else {
				parsedData[groupIndex].trans[transIndex].ru = {
					male: entryRu,
					female: ''
				};
			}
		}
	}

	async function handleFileInput(e: Event) {
		const input = e.target as HTMLInputElement;
		const file = input?.files?.[0];
		if (!file) return;

		try {
			loadedFilename = file.name;
			const content = await file.text();
			parsedData = parseFile(content);
			console.log(parsedData);
		} catch (err) {
			console.error('Error reading file:', err instanceof Error ? err.message : err);
		}
	}

	import autosize from 'svelte-autosize';
</script>

<div class="flex flex-col gap-2 py-4 items-center justify-center relative">
	<h1 class="text-xl font-semibold text-center pr-2">
        LOCALIZATION ENTRY TOOL
        {#if parsedData.length > 0}
            <span class="text-base-neutral">
                ({parsedData.reduce((sum, obj) => sum + obj.trans.length, 0)} entries)
            </span>
        {/if}
    </h1>

	<div class="join">
		<input
			type="file"
			class="file-input file-input-accent join-item"
			onchange={handleFileInput}
		/>
		<button
			class="btn btn-success join-item"
			onclick={handleFileExport}
			disabled={loadedFilename === ''}
		>
			Export
		</button>
	</div>
</div>

<div class="w-[70em] mx-auto rounded-sm border-2 border-neutral bg-base-100">
	<table class="table table-fixed">
		<thead class="border-b-2 font-bold">
			<tr>
				<td>Category</td>
				<td class="w-[40%] border-x-2">English</td>
				<td class="w-[40%] border-x-2">Russian</td>
				<td class="w-[5%]">M/F</td>
			</tr>
		</thead>

		<tbody>
			{#each parsedData as groupEntry, groupIndex}
				{#each groupEntry.trans as entry, index}
					<tr class="border-neutral/60 border-b-2">
						{#if index === 0}
							<td rowspan={groupEntry.trans.length} class="text-center text-base">
								{groupEntry.group}
								{#if groupEntry.subgroup}
									<br />
									<br />
									<span
										class="font-semibold"
										class:text-secondary={groupEntry.subgroup === 'Personality'}
										class:text-info={groupEntry.subgroup === 'Skill'}
									>
										[{groupEntry.subgroup}]
									</span>
								{/if}
							</td>
						{/if}
						<td
							class="whitespace-pre-wrap self-center text-base border-neutral/60 border-l-2 "
							>{entry.eng}</td
						>
						<td
							class="p-0 border-neutral/60 border-x-2"
						>
							<div class="flex h-full w-full">
								{#if isGenderedEntry(entry.ru)}
									<textarea
										class="flex-1 py-3 px-2 text-base bg-info/50"
										class:bg-notify-untranslated={entry.ru.male === ''}
										bind:value={entry.ru.male}
										rows="1"
										use:autosize
									>
									</textarea>
									<textarea
										class="flex-1 py-3 px-2 text-base bg-primary-content"
										class:bg-notify-untranslated={entry.ru.female === ''}
										bind:value={entry.ru.female}
										rows="1"
										use:autosize
									>
									</textarea>
								{:else}
									<textarea
										class="flex-1 py-3 px-2 text-base"
										class:bg-notify-untranslated={entry.eng.toLowerCase() ===
											entry.ru.toLowerCase()}
										bind:value={entry.ru}
										rows="1"
										use:autosize
									>
									</textarea>
								{/if}
							</div>
						</td>
						<td>
							<input
								type="checkbox"
								class="checkbox checkbox-info"
								checked={isGenderedEntry('string')}
								onchange={() => {
									changeEntryType(groupIndex, index);
								}}
							/>
						</td>
					</tr>
				{/each}
			{/each}
		</tbody>
	</table>
</div>
