<script>

	// import '../../../css/global.css';

	export let isOpen = false;
	export let close;

	const handleEvents = (event) => {
		if (event.data === "close-popup") {
			close();
		}
	}

	import { onMount, onDestroy } from 'svelte';

	onMount(() => {
		window.addEventListener('message', handleEvents);

		return () => {
			window.removeEventListener('message', handleEvents);
		}
	});
</script>

<style>
	iframe {
		display: block;
		width: 100%;
		height: 100%;
	}
</style>

{#if isOpen}
	<iframe src="/popup" frameborder="0" allowfullscreen></iframe>
{/if}