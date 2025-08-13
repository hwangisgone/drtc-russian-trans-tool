<script lang="ts">
	type Translation = {
		eng: string;
		ru: string;
		times?: number;
		strict?: boolean;

		samelength?: boolean;
	};

	let transList: Translation[] = $state([
		// Title
		{ eng: '  START  ', ru: '  СТАРТ  ' },
		// { eng: 'UNLOCKS', ru: 'ГОРОДОК' },
		// { eng: 'Official Discord', ru: 'Офф Дискорд' },
		{ eng: 'Madgarden & Rocketcat Games', ru: 'Мэдгарден и Рокеткэт Геймс' },
		{ eng: 'LOADING', ru: 'ЖДИТЕ' },

		// Settings
		{ eng: 'SETTINGS', ru: 'КОНФИГ', strict: true, times: 2 },
		{ eng: 'QUIT', ru: 'УЙТИ', times: 2 },

		{ eng: 'P1 Controls', ru: 'Р1 Кнопки  ' },
		{ eng: 'P2 Controls', ru: 'Р2 Кнопки' },
		{ eng: 'P3 Controls', ru: 'Р3 Кнопки' },
		{ eng: 'P4 Controls', ru: 'Р4 Кнопки' },
		{ eng: 'Controls', ru: 'Кнопки' },
		{ eng: 'Sound', ru: 'Звук' },
		{ eng: 'Game Music', ru: 'Музыка' },
		{ eng: 'Scratch', ru: 'Пленка' },
		{ eng: 'Grain', ru: 'Рябь' },
		{ eng: 'Glitch', ru: 'Гличи' },
		{ eng: 'Fast Text', ru: 'Быс Текст' },
		{ eng: 'Go windowed', ru: 'Оконный' },
		{ eng: 'Fullscreen SOFT', ru: 'fullscreen soft' },
		{ eng: 'Fullscreen HARD', ru: 'fullscreen hard' },
		{ eng: 'Window size', ru: 'Размер окна' },
		{ eng: 'VSYNC', ru: 'vsync' },
		{ eng: 'PLAYER 1 INPUT', ru: 'Р1 Ввод' },
		{ eng: 'PLAYER 2 INPUT', ru: 'Р2 Ввод' },
		{ eng: 'PLAYER 3 INPUT', ru: 'Р3 Ввод' },
		{ eng: 'PLAYER 4 INPUT', ru: 'Р4 Ввод' },
		{ eng: 'Up', ru: 'up' },
		{ eng: 'Left', ru: 'left' },
		{ eng: 'Down', ru: 'down' },
		{ eng: 'Right', ru: 'right' },
		{ eng: 'Prev', ru: 'prev' },
		{ eng: 'Attack', ru: 'attack' },
		{ eng: 'Use', ru: 'use' },
		{ eng: 'Swap', ru: 'swap' },
		{ eng: 'Next', ru: 'next' },
		{ eng: 'Deadzone', ru: 'deadzone' },
		{ eng: 'L-stick', ru: 'l-stick' },
		{ eng: 'R-stick', ru: 'r-stick' },
		{ eng: 'D-pad', ru: 'd-pad' },
		// { eng: 'NO JOY', ru: 'НЕТДЖО' },
		{ eng: 'PRESS!', ru: 'press!' },
		{ eng: 'IN USE', ru: 'in use' },
		{ eng: 'JOY1', ru: 'ДЖО1' },
		{ eng: 'RESET', ru: 'СБРОС' },

		// Custom characters
		{ eng: 'Custom Character', ru: 'Кастомный Герой' },
		{ eng: 'BODY SETTINGS', ru: 'НАСТРОЙ ТЕЛО' },
		{ eng: 'HEAD SETTINGS', ru: 'НАСТРОЙ ХЭД' },
		{ eng: 'HEAD', ru: 'head' },
		{ eng: 'BODY', ru: 'body' },
		{ eng: 'NAME', ru: 'ИМЯ' }, // Good thing it's the highest
		{ eng: 'PERK', ru: 'ПЕРК', times: 2 }, // x2
		{ eng: 'TRAIT', ru: 'ЧЕРТА', times: 2 }, // x2 ?
		{ eng: 'SELECT PERK', ru: 'ВЫБОР ПЕРКА' },
		{ eng: 'SELECT TRAIT', ru: 'ВЫБОР ЧЕРТЫ' },
		{ eng: 'Nope', ru: 'Нет' },
		{ eng: 'Good', ru: 'Ок' },
		{ eng: 'Nuts', ru: 'nuts' },
		{ eng: ' GENDER ', ru: ' gender ' },
		{ eng: ' TOP ', ru: ' top ' },
		{ eng: ' SIZE ', ru: ' size ' },
		{ eng: ' BOTTOMS ', ru: ' bottoms ' },
		{ eng: ' FACE ', ru: ' face ' },
		{ eng: ' SKIN CLR ', ru: ' skin clr ' },
		{ eng: ' HAIR ', ru: ' hair ' },
		{ eng: ' HAIR CLR ', ru: ' hair clr ' },
		{ eng: ' HAT ', ru: ' hat ' },
		{ eng: ' SHADES ', ru: ' shades ' },
		{ eng: ' EXTRA ', ru: ' extra ' },
		{ eng: 'Random', ru: 'random', times: 2 }, // x2
		{ eng: 'Save', ru: 'Сохр', strict: true, times: 1 },
		{ eng: 'Load', ru: 'Загр', strict: true, times: 2 }, // x2
		{ eng: 'SAVE', ru: 'СОХР' }, // strict? can't
		{ eng: 'LOAD', ru: 'ЗАГР', strict: true },
		{ eng: ' USED ', ru: ' used ' },
		{ eng: ' PAGE ', ru: ' page ' },
		{ eng: 'DELETE CUSTOM CHARACTER', ru: 'УДАЛИТЬ КАСТОМ ГЕРОЯ' },
		{ eng: "DELETE existing '%s' character?", ru: "УДАЛИТЬ персонажа '%s' ?" },
		{ eng: 'Keep', ru: 'Оста' },
		{ eng: 'DELETE', ru: 'УБРАТЬ' },
		{ eng: 'empty', ru: 'пусто' }, // Only replace the first "empty"

		// New game UI
		{ eng: 'Game Mode', ru: 'Режим' },
		{ eng: 'Leader', ru: 'Лидер' },
		{ eng: 'Buddy', ru: 'Друг', strict: true },
		{ eng: 'Maybe later', ru: 'Может позже' },
		{ eng: 'NAH', ru: 'НЕТ' },
		{ eng: 'OK', ru: 'ОК', times: 2, strict: true }, // It's hard to find a similar word & There are many OK
		{ eng: 'With buddy', ru: 'С другом' },
		{ eng: 'No buddy', ru: 'Без него' },
		{ eng: 'Load Random', ru: 'Загр Рандом' },
		{ eng: 'Start', ru: 'Старт', times: 2, strict: true },

		// Road UI
		{ eng: 'Vehicle', ru: 'Машина' },
		{ eng: 'Status', ru: 'Статус', times: 3 },
		{ eng: 'Equip', ru: 'Эквип', times: 2 },
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
		{ eng: 'LOOT in the car: ', ru: 'ДОБЫЧА в машине: ' },
		{ eng: 'nothing', ru: 'ничего' },
		{ eng: 'in the car', ru: 'в машине' },

		{ eng: 'Gotcha', ru: 'Сюдааа' },

		// Road events, CYOAs
		{ eng: 'GET', ru: 'get', strict: true },
		{ eng: 'LOSE', ru: 'lose', strict: true },
		{ eng: 'food', ru: 'еда ', samelength: true },
		{ eng: 'gas', ru: 'газ', strict: true, samelength: true },
		{ eng: 'medi', ru: 'medi', samelength: true },
		{ eng: 'cal', ru: 'cal', samelength: true }, // medical, appears on top
		{ eng: 'shotgun ammo', ru: 'дробь' },
		{ eng: 'rifle ammo', ru: 'ружейный' },
		{ eng: 'pistol ammo', ru: 'пульки' },
		{ eng: 'increases', ru: 'расти' },
		{ eng: 'decreases', ru: 'убывать' },
		{ eng: '%s revealed', ru: '%s выявил' },

		// MISSION SUMMARY
		{ eng: 'total %s', ru: 'всего %s' },
		{ eng: 'Loot', ru: 'Лут' },
		{ eng: 'Gear', ru: 'Вещи' },
		{ eng: 'CARRYING:', ru: 'НЕСЕТ:' },

		{ eng: 'SELECT CHARACTER', ru: 'ВЫБЕРИ ПЕРСОНАЖА' },
		{ eng: 'Press START to JOIN!', ru: 'Нажми СТАРТ!' },

		{ eng: 'Choose UR Fate', ru: 'ТВОЯ судьба' },
		{ eng: 'MORE...', ru: 'БОЛЬШЕ' },

		// { eng: 'uese', ru: 'исп' },
		// Others
		{ eng: 'yoink', ru: 'йонк' },
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

	const reversedSymbolMap: Record<number, string> = {
		0: '',
		64: 'А',
		65: 'Б',
		66: 'В',
		67: 'Г',
		68: 'Д',
		69: 'Е',
		70: 'Ж',
		71: 'З',
		72: 'И',
		73: 'Й',
		74: 'К',
		75: 'Л',
		76: 'М',
		77: 'Н',
		78: 'О',
		79: 'П',
		80: 'Р',
		81: 'С',
		82: 'Т',
		83: 'У',
		84: 'Ф',
		85: 'Х',
		86: 'Ц',
		87: 'Ч',
		88: 'Ш',
		89: 'Щ',
		90: 'Ъ',
		91: 'Ы',
		92: 'Ь',
		93: 'Э',
		94: 'Ю',
		95: 'Я',
		160: 'а',
		161: 'б',
		162: 'в',
		163: 'г',
		164: 'д',
		165: 'е',
		166: 'ж',
		167: 'з',
		168: 'и',
		169: 'й',
		170: 'к',
		171: 'л',
		172: 'м',
		173: 'н',
		174: 'о',
		175: 'п',
		192: 'р',
		193: 'с',
		194: 'т',
		195: 'у',
		196: 'ф',
		197: 'х',
		198: 'ц',
		199: 'ч',
		200: 'ш',
		201: 'щ',
		202: 'ъ',
		203: 'ы',
		204: 'ь',
		205: 'э',
		206: 'ю',
		207: 'я'
	};

	const extraTransList = [{ eng: 'fonts/font6x8.png', replaced: 'fonts/ront6x8.png' }];

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

	// Remove nontranslation

	if (browser) {
		let transListStr = sessionStorage.getItem('transList');
		if (transListStr) {
			transList = JSON.parse(transListStr);
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

				const newList = JSON.parse(text);
				transList = reverseTranslate(newList);

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

	function reverseTranslate(oldList: (Translation & { replaced: string })[]) {
		const oldTransMap = new Map(oldList.map((item) => [item.eng, item]));
		const result = [];

		for (const item of transList) {
			const oldItem = oldTransMap.get(item.eng);

			if (oldItem) {
				// Reverse translate the 'replaced' field to get new 'ru' value
				const reversedRu = Array.from(oldItem.replaced)
					.map((c) => reversedSymbolMap[c.charCodeAt(0)] ?? c)
					.join('');

				// Use newer item data as base but replace 'ru' with reversed translation from old
				const resultItem = {
					...item,
					ru: reversedRu
				};

				result.push(resultItem);
			} else {
				result.push(item);
			}
		}

		return result;
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
			...newTransList.map(({ ru, samelength, ...rest }) => rest)
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
							class:bg-notify-untranslated={trans.eng.toLowerCase() ===
								trans.ru.toLowerCase()}
							bind:value={trans.ru}
							rows="1"
							use:autosize
						>
						</textarea>
					</td>
					<td
						class:bg-warning={trans.samelength && trans.eng.length > trans.ru.length}
						class:bg-success={trans.samelength
							? trans.eng.length === trans.ru.length
							: trans.eng.length >= trans.ru.length}
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
