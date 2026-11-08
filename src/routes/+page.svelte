<script>
	import { resolve } from '$app/paths';
</script>

<svelte:head>
	<title>Home | Arcade</title>
	<meta name="description" content="Explore my crossword puzzle and 2048 arcade games." />
</svelte:head>

<h1>Welcome to My Crossword Puzzle Game</h1>

<p>
	I designed this mini crossword puzzle myself, and I hope you enjoy playing it. If you get stuck,
	use the clues, think creatively, and keep trying.
</p>

<a href={resolve('/crossword')}>Play Crossword</a>
