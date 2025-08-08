<script lang="ts">
	type Translation = {
		eng: string;
		ru: string;
		times?: number;
		strict?: boolean;
	};

	let transList: Translation[] = $state([
		// Title
		{ eng: '  START  ', ru: '  СТАРТ  ' },
		// { eng: 'UNLOCKS', ru: 'ГОРОДОК' },
		// { eng: 'Official Discord', ru: 'Офф Дискорд' },
		{ eng: 'Madgarden & Rocketcat Games', ru: 'Мadgarden & Яocketcat Гames' },
		{ eng: 'LOADING', ru: 'ЖДИТЕ' },

		// Settings
		{ eng: 'SETTINGS', ru: 'Конфиг', strict: true, times: 2 },
		{ eng: 'QUIT', ru: 'ВЫЙТ', times: 2 },

		{ eng: 'P1 Controls', ru: 'Р1 Кнопки' },
		{ eng: 'P2 Controls', ru: 'Р2 Кнопки' },
		{ eng: 'P3 Controls', ru: 'Р3 Кнопки' },
		{ eng: 'P4 Controls', ru: 'Р4 Кнопки' },
		{ eng: 'Controls', ru: 'Управл' },
		{ eng: 'Sound', ru: 'Звук' },
		{ eng: 'Game Music', ru: 'Музыка' },
		{ eng: 'Scratch', ru: 'Пленка' },
		{ eng: 'Grain', ru: 'Рябь' },
		{ eng: 'Glitch', ru: 'Гличи' },
		{ eng: 'Fast Text', ru: 'Быс Текст' },
		{ eng: 'Go windowed', ru: 'Оконный' },
		{ eng: 'Fullscreen SOFT', ru: 'Фуллскрин СОФТ' },
		{ eng: 'Fullscreen HARD', ru: 'Фуллскрин ХАРД' },
		{ eng: 'Window size', ru: 'Размер окна' },
		{ eng: 'VSYNC', ru: 'ВСИНК' },
		{ eng: 'PLAYER 1 INPUT', ru: 'Р1 Ввод' },
		{ eng: 'PLAYER 2 INPUT', ru: 'Р2 Ввод' },
		{ eng: 'PLAYER 3 INPUT', ru: 'Р3 Ввод' },
		{ eng: 'PLAYER 4 INPUT', ru: 'Р4 Ввод' },
		{ eng: 'Up', ru: 'Ап' },
		{ eng: 'Left', ru: 'Лево' },
		{ eng: 'Down', ru: 'Вниз' },
		{ eng: 'Right', ru: 'Право' },
		{ eng: 'Prev', ru: 'Пред' },
		{ eng: 'Attack', ru: 'Атака' },
		{ eng: 'Use', ru: 'Исп' },
		{ eng: 'Swap', ru: 'Смен' },
		{ eng: 'Next', ru: 'След' },
		{ eng: 'Deadzone', ru: 'Дэдзона' },
		{ eng: 'L-stick', ru: 'Л-стик' },
		{ eng: 'R-stick', ru: 'П-стик' },
		{ eng: 'D-pad', ru: 'Д-пад' },
		// { eng: 'NO JOY', ru: 'НЕТДЖО' },
		{ eng: 'JOY1', ru: 'ДЖО1' },
		{ eng: 'RESET', ru: 'Сброс' },

		// Custom characters
		{ eng: 'Custom Character', ru: 'Кастомный Герой' },
		{ eng: 'BODY SETTINGS', ru: 'НАСТРОЙ ТЕЛО' },
		{ eng: 'HEAD SETTINGS', ru: 'НАСТРОЙ ХЭД' },
		{ eng: 'HEAD', ru: 'ХЭД' },
		{ eng: 'BODY', ru: 'ТЕЛО' },
		{ eng: 'NAME', ru: 'ИМЯ' }, // Good thing it's the highest
		{ eng: 'PERK', ru: 'ПЕРК', times: 2 }, // x2
		{ eng: 'TRAIT', ru: 'ЧЕРТА', times: 2 }, // x2 ?
		{ eng: 'SELECT PERK', ru: 'ВЫБОР ПЕРКА' },
		{ eng: 'SELECT TRAIT', ru: 'ВЫБОР ЧЕРТЫ' },
		{ eng: 'Nope', ru: 'Нет' },
		{ eng: 'Good', ru: 'Ок' },
		{ eng: 'Nuts', ru: 'nuts' },
		{ eng: ' GENDER ', ru: ' ПОЛ ' },
		{ eng: ' TOP ', ru: ' ТОП ' },
		{ eng: ' SIZE ', ru: ' РАЗМ ' },
		{ eng: ' BOTTOMS ', ru: ' ОБУВЬ ' },
		{ eng: ' FACE ', ru: ' ЛИЦО ' },
		{ eng: ' SKIN CLR ', ru: ' ЦВТ КОЖИ ' },
		{ eng: ' HAIR ', ru: ' hair ' },
		{ eng: ' HAIR CLR ', ru: ' hair clr ' },
		{ eng: ' HAT ', ru: ' hat ' },
		{ eng: ' SHADES ', ru: '  ОЧКИ  ' },
		{ eng: ' EXTRA ', ru: '  ДОП  ' },
		{ eng: 'Random', ru: 'Рандом', times: 2 }, // x2
		{ eng: 'Save', ru: 'Сохр', strict: true, times: 1 },
		{ eng: 'Load', ru: 'Загр', strict: true, times: 2 }, // x2
		{ eng: 'SAVE', ru: 'СОХР' }, // strict? can't
		{ eng: 'LOAD', ru: 'ЗАГР', strict: true },
		{ eng: ' USED ', ru: ' ИСП  ' },
		{ eng: ' PAGE ', ru: ' СТР  ' },
		{ eng: 'DELETE CUSTOM CHARACTER', ru: 'УДАЛИТЬ КАСТОМ ГЕРОЯ' },
		{ eng: "DELETE existing '%s' character?", ru: "delete existing '%s' character?" },
		{ eng: 'Keep', ru: 'Оста' },
		{ eng: 'DELETE', ru: 'УБРАТЬ' },
		{ eng: 'empty', ru: 'пусто' }, // Only replace the first "empty"

		// New game UI
		{ eng: 'Game Mode', ru: 'Режим' },
		{ eng: 'Leader', ru: 'Лидер' },
		{ eng: 'Buddy', ru: 'Друг', strict: true },
		{ eng: 'Maybe later', ru: 'Может позже' },
		{ eng: 'NAH', ru: 'НЕТ' },
		{ eng: 'OK', ru: 'ok', times: 2, strict: true }, // It's hard to find a similar word & There are many OK
		{ eng: 'With buddy', ru: 'С другом' },
		{ eng: 'No buddy', ru: 'Без него' },
		{ eng: 'Load Random', ru: 'Загр Рандом' },
		{ eng: 'Start', ru: 'Старт', times: 2, strict: true },

		// Road UI
		{ eng: 'Vehicle', ru: 'Машина' },
		{ eng: 'Status', ru: 'Статус' },
		{ eng: 'Equip', ru: 'Эквип' },
		{ eng: 'Wield', ru: 'Глав' },
		{ eng: 'Carry', ru: 'Втор' },
		{ eng: 'fuel', ru: 'топл', strict: true },
		{ eng: 'speed', ru: 'темп', strict: true },

		// Before Mission
		{ eng: 'Role', ru: 'Роль' },
		{ eng: 'ROLE:', ru: 'РОЛЬ:', strict: true },
		{ eng: 'LEAD', ru: 'ВЕДИ', strict: true },
		{ eng: 'FOLLOW', ru: 'СЛЕДУЙ' },
		{ eng: 'REST', ru: 'СОН' },
		{
			eng: 'ROLE:\n\nLead the mission through the scavenging site.\n\nControlled by PLAYER.',
			ru: 'РОЛЬ:\n\nЛидер миссии\n\nКонтролирует ИГРОК.'
		},
		{
			eng: 'ROLE:\n\nFollow and assist the lead member.',
			ru: 'РОЛЬ:\n\nСледует за лидером и помогает ему.'
		},
		{
			eng: 'ROLE:\n\nRest and recover from afar while guarding team supplies.',
			ru: 'РОЛЬ:\n\nОтдыхает и восстанавливается пока охраняет ресурсы.'
		},

		// Mission UI
		{ eng: 'Team', ru: 'Кмнд' },
		{ eng: 'Swap Meet', ru: 'Обмен' },
		{ eng: 'COMBAT >>>', ru: 'БОЙ >>>' },
		{ eng: 'SMASHIN!', ru: 'БЛИЖНИЙ!' },
		{ eng: 'EITHER', ru: 'ЛЮБОЙ' },
		{ eng: 'SHOOTIN!', ru: 'ДАЛЬНИЙ!' },
		{ eng: 'TACTIC >>>', ru: 'РЕЖИМ >>>' },
		{ eng: 'FIGHTIN!', ru: 'РЕЗНЯ!' },
		{ eng: 'DEFEND', ru: 'ЗАЩИТА' },
		{ eng: 'RUNNIN!', ru: 'БЕГ!' },
		{ eng: 'Trunk', ru: 'Багаж' },
		{ eng: 'LOOT in the car: ', ru: 'loot in the car: ' },
		{ eng: 'nothing', ru: 'nothing' },
		{ eng: 'in the car', ru: 'in the car' },

		{ eng: 'Gotcha', ru: 'Сюдааа' },

		// Road events, CYOAs
		{ eng: 'GET', ru: 'ГЕТ', strict: true },
		{ eng: 'LOSE', ru: 'ЛУЗ', strict: true },
		{ eng: 'food', ru: 'food' },
		{ eng: 'gas', ru: 'газ', strict: true },
		{ eng: 'medi', ru: 'medi' },
		{ eng: 'cal', ru: 'cal' }, // medical, appears on top
		{ eng: 'shotgun ammo', ru: 'дробь' },
		{ eng: 'rifle ammo', ru: 'rifle ammo' },
		{ eng: 'pistol ammo', ru: 'пульки' },
		{ eng: 'increases', ru: 'расти' },
		{ eng: 'decreases', ru: 'убывать' },
		{ eng: '%s revealed', ru: '%s выявил' },

		// MISSION SUMMARY
		{ eng: 'total %s', ru: 'всего %s' },
		{ eng: 'Loot', ru: 'Лут' },
		{ eng: 'Gear', ru: 'Вещи' },
		{ eng: 'CARRYING:', ru: 'CARRYING:' },

		{ eng: 'SELECT CHARACTER', ru: 'SELECT CHARACTER' },
		{ eng: 'Press START to JOIN!', ru: 'Press START to JOIN!' },

		{ eng: 'Choose UR Fate', ru: 'ТВОЯ судьба' },
		{ eng: 'MORE...', ru: 'БОЛЬШЕ' },

		// { eng: 'uese', ru: 'исп' },
		// Others
		{ eng: 'yoink', ru: 'yoink' },
		{ eng: '* SNAP *', ru: '* snap *' },

		{ eng: 'YOU HAVE DIED', ru: 'ВЫ УМЕРЛИ' },
		{ eng: 'on the', ru: 'на' },
		{ eng: 'DANG IT', ru: 'ОКАК' }
	]);

	const symbolMap: Record<string, number> = {
		А: 64,
		Б: 65,
		В: 66,
		Г: 67,
		Д: 68,
		Е: 69,
		Ж: 70,
		З: 71,
		И: 72,
		Й: 73,
		К: 74,
		Л: 75,
		М: 76,
		Н: 77,
		О: 78,
		П: 79,
		Р: 80,
		С: 81,
		Т: 82,
		У: 83,
		Ф: 84,
		Х: 85,
		Ц: 86,
		Ч: 87,
		Ш: 88,
		Щ: 89,
		Ъ: 90,
		Ы: 91,
		Ь: 92,
		Э: 93,
		Ю: 94,
		Я: 95,
		а: 160,
		б: 161,
		в: 162,
		г: 163,
		д: 164,
		е: 165,
		ж: 166,
		з: 167,
		и: 168,
		й: 169,
		к: 170,
		л: 171,
		м: 172,
		н: 173,
		о: 174,
		п: 175,
		р: 192,
		с: 193,
		т: 194,
		у: 195,
		ф: 196,
		х: 197,
		ц: 198,
		ч: 199,
		ш: 200,
		щ: 201,
		ъ: 202,
		ы: 203,
		ь: 204,
		э: 205,
		ю: 206,
		я: 207
	};

	
	const extraTransList = [
		{ eng: 'fonts/font6x8.png', replaced: 'fonts/ront6x8.png' }
	];

	function compareSign(len1: number, len2: number) {
		if (len1 > len2) {
			return '>';
		} else if (len1 < len2) {
			return '<';
		} else {
			return '=';
		}
	}

	import autosize from 'svelte-autosize';

	import { browser } from '$app/environment';

	let exportCount = $state(0);

	// Method 1: Simple merge - array2 overrides array1
	function mergeTranslationShallow(arr1: Translation[], arr2: Translation[], excludeArr: { eng: string }[] = []) {
		const map = new Map();
		const excludedSet = new Set(excludeArr.map(o => o.eng));

		// Add all items from first array
		for (const item of arr1) {
			map.set(item.eng, { ...item });
		}

		// Override/add items from second array
		for (const item of arr2) {
			if (map.has(item.eng)) {
				map.set(item.eng, { ...map.get(item.eng), ...item });
			} else {
				if (!excludedSet.has(item.eng)) {
					map.set(item.eng, { ...item });
				}
			}
		}

		return Array.from(map.values());
	}

	if (browser) {
		let transListStr = sessionStorage.getItem('transList');
		if (transListStr) {
			transList = mergeTranslationShallow(
				(() => $state.snapshot(transList))(),
				JSON.parse(transListStr)
			);
		}

		exportCount = Number(
			sessionStorage.getItem('exportCount') ?? (() => $state.snapshot(transList).length)()
		);
	}

	function handleImport() {
		const input = document.createElement('input');
		input.type = 'file';
		input.accept = 'application/json';

		input.onchange = async () => {
			const file = input.files?.[0];
			if (!file) return;

			try {
				const text = await file.text();

				// Merge: newer items override based on `eng` key
				// Also exlude items in extraTransList
				const newList = JSON.parse(text);
				transList = mergeTranslationShallow(transList, newList, extraTransList);

				alert('Loaded translation JSON file.');
			} catch (err) {
				alert('Invalid translation JSON file.');
			}

			input.remove();
		};

		input.click();
	}

	function handleExportCounter(e: Event) {
		const val = (e.target as HTMLInputElement).value;
		if (browser) {
			sessionStorage.setItem('exportCount', val);
		}
	}

	function translate() {
		// Save current transList
		if (browser) {
			sessionStorage.setItem('transList', JSON.stringify(transList));
		}

		const newTransList: (Translation & { replaced?: string })[] = [...transList];

		for (const trans of newTransList) {
			trans.replaced = Array.from(trans.ru)
				.map((c) => (symbolMap[c] ? String.fromCharCode(symbolMap[c]) : c))
				.join('');

			if (trans.eng.length > trans.replaced.length) {
				trans.replaced = trans.replaced.padEnd(trans.eng.length, '\0');
			}
		}

		const refinedTransList = [
			...extraTransList,
			...newTransList.map(({ ru, ...rest }) => rest)
		];

		console.log(refinedTransList);

		// Create downloadable file
		const blob = new Blob([JSON.stringify(refinedTransList.slice(0, exportCount + 1))], {
			type: 'application/json'
		});

		const url = URL.createObjectURL(blob);
		const a = document.createElement('a');
		a.href = url;
		a.download = 'exe_ru.json';
		document.body.appendChild(a);
		a.click();
		document.body.removeChild(a);
		URL.revokeObjectURL(url);
	}
</script>

<div class="flex justify-center items-center gap-4 py-4">
	<button class="btn btn-accent" onclick={handleImport}>Import</button>
	<h1 class="text-lg font-semibold">TRANSLATION TOOL</h1>
	<button class="btn btn-info" onclick={translate}>Export</button>
	<input
		type="number"
		max={transList.length}
		class="input w-20"
		bind:value={exportCount}
		onchange={handleExportCounter}
	/>
</div>

<div class="w-[55em] mx-auto rounded-sm border-2 border-neutral bg-base-100">
	<table class="table table-fixed">
		<thead>
			<tr class="border-base-300 border-b-2">
				<td class="w-[44%] font-bold">English</td>
				<td class="w-[44%] font-bold border-x-2 border-base-300">Russian</td>
				<td class="font-bold p-0 text-center">Valid length</td>
			</tr>
		</thead>

		<tbody>
			{#each transList as trans}
				<tr class="border-base-300 border-b-2 border-l-2">
					<td class="whitespace-pre-wrap self-center text-base border-r-2 border-base-300"
						>{trans.eng}</td
					>
					<td class="p-0">
						<textarea
							class="h-full w-full block py-3 px-2 text-base"
							class:bg-notify-untranslated={trans.eng.toLowerCase() === trans.ru.toLowerCase()}
							bind:value={trans.ru}
							rows="1"
							use:autosize
						>
						</textarea>
					</td>
					<td
						class:bg-success={trans.eng.length >= trans.ru.length}
						class="bg-error py-1 px-2 text-base-100 font-semibold text-center"
					>
						{trans.eng.length}
						{compareSign(trans.eng.length, trans.ru.length)}
						{trans.ru.length}
					</td>
				</tr>
			{/each}
		</tbody>
	</table>
</div>


<style>
	.bg-notify-untranslated {
		background-color: oklch(0.8065 0.0773 60.729);
	}
</style>