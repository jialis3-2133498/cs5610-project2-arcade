<script>
	/** @type {{ value: number }} */
	let { value } = $props();

	/** @type {Record<number, { background: string, text: string }>} */
	const tileColors = {
		2: { background: '#EEE4DA', text: '#40362B' },
		4: { background: '#E8D6B9', text: '#40362B' },
		8: { background: '#E4C79D', text: '#40362B' },
		16: { background: '#D9B78E', text: '#403020' },
		32: { background: '#CDA57A', text: '#302217' },
		64: { background: '#BE9268', text: '#24180F' },
		128: { background: '#AE805A', text: '#17110B' },
		256: { background: '#936946', text: '#FFFFFF' },
		512: { background: '#805939', text: '#FFFFFF' },
		1024: { background: '#704B2E', text: '#FFFFFF' },
		2048: { background: '#5C3B24', text: '#FFFFFF' },
		4096: { background: '#49301E', text: '#FFFFFF' }
	};

	let tileColor = $derived(tileColors[value] ?? { background: '#49301E', text: '#FFFFFF' });
</script>

<div
	class="tile"
	style:background-color={value === 0 ? '#D3C8B9' : tileColor.background}
	style:color={tileColor.text}
>
	{#if value !== 0}
		{value}
	{/if}
</div>

<style>
	.tile {
		aspect-ratio: 1;
		display: flex;
		justify-content: center;
		align-items: center;

		font-size: clamp(0.875rem, 4vw, 1.5rem);
		font-weight: bold;
		border-radius: 4px;
	}
</style>
