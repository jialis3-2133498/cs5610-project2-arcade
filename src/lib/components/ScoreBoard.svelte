<script>
	let { score, bestScore } = $props();
</script>

<div class="scoreboard">
	<div class="score">
		<h2>Score</h2>
		<p>{score}</p>
	</div>

	<div class="best-score">
		<h2>Best Score</h2>
		<p>{bestScore}</p>
	</div>
</div>

<style>
	.scoreboard {
		display: flex;
		gap: 12px;
		width: 100%;
		max-width: 400px;
	}
	.score,
	.best-score {
		flex: 1;
		background-color: #dac292;
		min-width: 0;
		padding: 12px 20px;
		border-radius: 8px;
		text-align: center;
	}

	.score h2,
	.best-score h2 {
		font-size: 1rem;
		margin: 0 0 0.5rem;
	}

	.score p,
	.best-score p {
		margin: 0;
	}

	@media (max-width: 480px) {
		.scoreboard {
			max-width: 280px;
		}

		.score,
		.best-score {
			padding: 0.5rem;
		}
	}
</style>
