<script lang="ts">
	import favicon from "$lib/assets/favicon.png";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}

<style>
	:global(body) {
		font-family: sans-serif;
		text-align: center;
	}
</style>
