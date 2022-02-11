<script>
	export let index;
	export let maxIndex;

	function handleKeyEvent(e) {
		if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') {
			if (index === 0) {
				index = maxIndex - 1;
			} else index = index - 1;
		}
		if (e.key === 'ArrowRight' || e.key === 'ArrowDown') {
			index = (index + 1) % maxIndex;
		}
	}
</script>

<svelte:window on:keydown={(e) => handleKeyEvent(e)} />
