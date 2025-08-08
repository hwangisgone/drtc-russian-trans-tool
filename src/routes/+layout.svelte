<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	import '../app.css';

	import { page } from '$app/state';

	let { children } = $props();

	const links = [
		{ href: '/', name: '.EXE ENTRY' },
		{ href: '/loc-entry', name: 'LOC ENTRY' }
	];
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="flex flex-col gap-2 absolute mx-4 my-4 z-10">
	{#each links as link}
		<a
			href={link.href}
			class="btn"
			class:bg-info={page.url.pathname === link.href}
			class:pointer-events-none={page.url.pathname === link.href}
		>
			{link.name}
		</a>
	{/each}
</div>

{@render children?.()}
