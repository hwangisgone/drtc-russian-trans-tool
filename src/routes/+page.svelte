<script lang="ts">
	const transList: {
		eng: string;
		replaced?: string;
		ru: string;
	}[] = $state([
		// Title
		{ eng: '  START  ', ru: '  СТАРТ  ' },
		{ eng: 'UNLOCKS', ru: 'ГОРОДОК' },
		{ eng: 'Official Discord', ru: 'Офф Дискорд' },
		{ eng: 'News Options', ru: 'Новости' },
		
		// Custom characters
		{ eng: 'BODY SETTINGS', ru: 'НАСТРОЙ ТЕЛО' },
		{ eng: 'HEAD SETTINGS', ru: 'НАСТРОЙ ХЭД' },

		{ eng: 'HEAD', ru: 'ХЭД' },
		{ eng: 'BODY', ru: 'ТЕЛО' },
		{ eng: 'NAME', ru: 'ИМЯ' },
		{ eng: 'PERK', ru: 'ПЕРК' },
		{ eng: 'TRAIT', ru: 'ЧЕРТА' },
	
		{ eng: 'GENDER', ru: 'ПОЛ' },
		{ eng: 'TOP', ru: 'ТОП' },
		{ eng: 'SIZE', ru: 'РАЗМ' },
		{ eng: 'BOTTOMS', ru: 'ОБУВЬ' },

		{ eng: 'FACE', ru: 'ЛИЦО' },
		{ eng: 'SKIN CLR', ru: 'ЦВТ КОЖИ' },
		{ eng: 'HAIR', ru: 'HAIR' },
		{ eng: 'HAIR CLR', ru: 'HAIR CLR' },
		{ eng: 'HAT', ru: 'HAT' },
		{ eng: 'SHADES', ru: 'ОЧКИ' },
		{ eng: 'EXTRA', ru: 'ДОП' },
		{ eng: 'Random', ru: 'Рандом' },
		{ eng: 'Save', ru: 'Сохр' },
		{ eng: 'Load', ru: 'Загр' },
		{ eng: 'SETTINGS', ru: 'Конфиг' },
		{ eng: 'QUIT', ru: 'Выйт' },
		{ eng: 'Controls', ru: 'Управл' },
		{ eng: 'P1 Controls', ru: 'Р1 Кнопки' },
		{ eng: 'P2 Controls', ru: 'Р2 Кнопки' },
		{ eng: 'P3 Controls', ru: 'Р3 Кнопки' },
		{ eng: 'P4 Controls', ru: 'Р4 Кнопки' },
		{ eng: 'Sound', ru: 'Звук' },
		{ eng: 'Scratch', ru: 'Пленка' },
		{ eng: 'Grain', ru: 'Рябь' },
		{ eng: 'Glitch', ru: 'Гличи' },
		{ eng: 'Fast Text', ru: 'Быс Текст' },
		{ eng: 'Go windowed', ru: 'Оконный' },
		{ eng: 'VSYNC', ru: 'ВСИНК' },
		{ eng: 'Fullscreen SOFT', ru: 'Фуллскрин СОФТ' },
		{ eng: 'Fullscreen HARD', ru: 'Фуллскрин ХАРД' },
		{ eng: 'Window size', ru: 'Размер окна' },
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
		{ eng: 'JOY1', ru: 'ДЖО1' },
		{ eng: 'RESET', ru: 'Сброс' },

		{ eng: 'SELECT PERK', ru: 'ВЫБОР ПЕРКА' },
		{ eng: 'SELECT TRAIT', ru: 'ВЫБОР ЧЕРТЫ' },
		{ eng: 'Vehicle', ru: 'Машина' },
		{ eng: 'Custom Character', ru: 'Кастомный Герой' },
		{ eng: 'NO JOY', ru: 'НЕТДЖО' },
		{ eng: 'Status', ru: 'Статус' },
		{ eng: 'Equip', ru: 'Эквип' },
		{ eng: 'Swap Meet', ru: 'Обмен' },
		{ eng: 'Team', ru: 'Кмнд' },
		{ eng: 'Game Music', ru: 'Музыка' },
		{ eng: 'Maybe later', ru: 'Может позже' },
		{ eng: 'NAH', ru: 'НЕТ' },
		{ eng: 'OK', ru: 'ОК' },
		{ eng: 'Gotcha', ru: 'Сюдааа' },
		{ eng: 'Start', ru: 'Старт' },
		{ eng: 'Load Random', ru: 'Загр Рандом' },
		{ eng: 'Leader', ru: 'Лидер' },
		{ eng: 'Buddy', ru: 'Друг' },
		{ eng: 'With buddy', ru: 'С другом' },
		{ eng: 'No buddy', ru: 'Без него' },
		{ eng: 'Game Mode', ru: 'Режим' },
		{ eng: 'RUNNIN!', ru: 'БЕГ!' },
		{ eng: 'COMBAT >>>', ru: 'БОЙ >>>' },
		{ eng: 'TACTIC >>>', ru: 'РЕЖИМ >>>' },
		{ eng: 'decreases', ru: 'убывать' },
		{ eng: 'LOSE', ru: 'ЛУЗ' },
		{ eng: 'food', ru: 'food' },
		{ eng: 'gas', ru: 'газ' },
		{ eng: 'GET', ru: 'ГЕТ' },
		{ eng: 'shotgun ammo', ru: 'дробь' },
		{ eng: 'rifle ammo', ru: 'rifle ammo' },
		{ eng: 'pistol ammo', ru: 'пульки' },
		{ eng: 'increases', ru: 'расти' },
		{ eng: 'Role', ru: 'Роль' },
		{ eng: 'DEFEND', ru: 'ЗАЩИТА' },
		{ eng: 'FIGHTIN!', ru: 'РЕЗНЯ!' },
		{ eng: 'SMASHIN!', ru: 'БЛИЖНИЙ!' },
		{ eng: 'EITHER', ru: 'ЛЮБОЙ' },
		{ eng: 'SHOOTIN!', ru: 'ДАЛЬНИЙ!' },
		{ eng: 'LEAD', ru: 'ВЕДИ' },
		{ eng: 'FOLLOW', ru: 'СЛЕДУЙ' },
		{ eng: 'REST', ru: 'СОН' },
		{ eng: 'Wield', ru: 'Глав' },
		{ eng: 'Carry', ru: 'Втор' },
		{ eng: 'DANG IT', ru: 'ОКАК' },
		{ eng: 'Loot', ru: 'Лут' },
		{ eng: 'Gear', ru: 'Вещи' },
		{ eng: 'Trunk', ru: 'Багаж' },


		{ eng: 'Keep', ru: 'Оста' },
		{ eng: 'DELETE', ru: 'УБРАТЬ' },
		{ eng: 'MORE...', ru: 'БОЛЬШЕ' },
		{ eng: 'NOPE', ru: 'НЕТ' },
		{ eng: 'SAVE', ru: 'СОХР' },
		{ eng: 'USED', ru: 'ИСП' },
		{ eng: 'PAGE', ru: 'СТР' },
		{ eng: 'fuel', ru: 'топл' },
		{ eng: 'speed', ru: 'темп' },
		{
			eng: 'ROLE:\n\nLead the mission through the scavenging site.\n\nControlled by PLAYER.',
			ru: 'ROLE:\n\nЛидер миссии\n\nКонтролирует ИГРОК.'
		},
		{
			eng: 'ROLE:\n\nFollow and assist the lead member.',
			ru: 'ROLE:\n\nСледует за лидером и помогает ему.'
		},
		{
			eng: 'ROLE:\n\nRest and recover from afar while guarding team supplies.',
			ru: 'ROLE:\n\nОтдыхает и восстанавливается пока охраняет ресурсы.'
		},
		{ eng: 'total %s', ru: 'всего %s' },
		{ eng: 'Choose UR Fate', ru: 'ТВОЯ судьба' },
		{ eng: 'DELETE CUSTOM CHARACTER', ru: 'УДАЛИТЬ КАСТОМ ГЕРОЯ' },
		{ eng: 'uese', ru: 'исп' },
		{ eng: 'Nope', ru: 'Нет' },
		{ eng: 'Good', ru: 'Ок' },
		{ eng: 'YOU HAVE DIED', ru: 'ВЫ УМЕРЛИ' },
		{ eng: 'on the', ru: 'на' },
		{ eng: 'LOADING', ru: 'ЖДИТЕ' }
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

	function translate() {
		for (const trans of transList) {
			trans.replaced = Array.from(trans.ru)
				.map((c) => (symbolMap[c] ? String.fromCharCode(symbolMap[c]) : c))
				.join('');
		}

		console.log(transList);
	}
</script>

<div class="justify-center items-center gap-4 flex">
	<h1 class="text-lg py-4 font-semibold">TRANSLATION TOOL</h1>
	<button class="btn btn-success" onclick={translate}>Export</button>
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
