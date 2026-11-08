<svelte:head>
	<title>Crossword | Jiali Sheng's Arcade</title>
	<meta name="description" content="Play my original mini crossword puzzle." />
</svelte:head>

<div class="game-main">
	<div class="game-heading">
		<h1>Mini Crossword Puzzle</h1>
		<section class="game-introduction">
			<h2>Game Introduction</h2>
			<p>
				Fill each open square with one letter. Use the Across and Down clues to solve the puzzle.
				Black squares do not contain letters. Some letters belong to both an Across and a Down
				answer.
			</p>
		</section>
	</div>

	<div class="game-content">
		<div class="puzzle-and-clues-container">
			<section>
				<h2>Puzzle</h2>
				<form>
					<div class="puzzle-grid">
						<div class="box open">
							<input
								type="text"
								maxlength="1"
								aria-label="Row 1, column 1, 1 Across and 1 Down"
							/><span class="clue-number" aria-hidden="true">1</span>
						</div>

						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 1, column 2, 1 Across" />
						</div>
						<div class="box open">
							<input
								type="text"
								maxlength="1"
								aria-label="Row 1, column 3, 1 Across and 2 Down"
							/><span class="clue-number" aria-hidden="true">2</span>
						</div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 2, column 1, 1 Down" />
						</div>
						<div class="box blocked"></div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 2, column 3, 2 Down" />
						</div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box open">
							<input
								type="text"
								maxlength="1"
								aria-label="Row 3, column 1, 3 Across and 1 Down"
							/><span class="clue-number" aria-hidden="true">3</span>
						</div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 3, column 2, 3 Across" />
						</div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 3, column 3, 3 Across and 2 Down" />
						</div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 3, column 4, 3 Across" />
						</div>
						<div class="box open">
							<input
								type="text"
								maxlength="1"
								aria-label="Row 3, column 5, 3 Across and 4 Down"
							/><span class="clue-number" aria-hidden="true">4</span>
						</div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 4, column 5, 4 Down" />
						</div>
						<div class="box blocked"></div>
						<div class="box blocked"></div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 5, column 3, 5 Across" /><span
								class="clue-number"
								aria-hidden="true">5</span
							>
						</div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 5, column 4, 5 Across" />
						</div>
						<div class="box open">
							<input type="text" maxlength="1" aria-label="Row 5, column 5, 5 Across and 4 Down" />
						</div>
					</div>
					<button class="clear-button" type="reset">Clear Puzzle</button>
				</form>
			</section>

			<section>
				<h2>Clues</h2>
				<section>
					<h3>Across</h3>
					<ol>
						<li value="1">A common pet that says "meow".</li>
						<li value="3">Evaluates or scores something.</li>
						<li value="5">What we breathe.</li>
					</ol>
				</section>

				<section>
					<h3>Down</h3>
					<ol>
						<li value="1">A vehicle you drive on the road.</li>
						<li value="2">A very young child.</li>
						<li value="4">A polite way to address a man.</li>
					</ol>
				</section>
			</section>
		</div>

		<section>
			<h2>Solution</h2>
			<details>
				<summary>Show solution</summary>

				<section>
					<h3>Across</h3>
					<ol>
						<li value="1">CAT</li>
						<li value="3">RATES</li>
						<li value="5">AIR</li>
					</ol>
				</section>

				<section>
					<h3>Down</h3>
					<ol>
						<li value="1">CAR</li>
						<li value="2">TOT</li>
						<li value="4">SIR</li>
					</ol>
				</section>
			</details>
		</section>
	</div>
</div>

<style>
	.puzzle-grid {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		max-width: var(--puzzle-size);
		margin: 0 auto;
		width: 100%;
	}
	.box {
		aspect-ratio: 1 / 1;
		position: relative;
	}

	.box input {
		width: 100%;
		height: 100%;
		padding: 0;
		font-size: var(--text-large);
		font-weight: bold;
		display: block;
		border: 1px solid var(--color-text);
		background-color: var(--color-puzzle-open);
		text-align: center;
		text-transform: uppercase;
	}
	.box input:focus-visible {
		outline: 2px solid var(--color-accent-dark);
		outline-offset: -3px;
	}

	.open {
		background-color: var(--color-puzzle-open);
	}
	.blocked {
		background-color: var(--color-puzzle-blocked);
	}

	.clue-number {
		position: absolute;
		top: 0.15rem;
		left: 0.2rem;

		font-size: var(--text-small);
		font-weight: bold;

		pointer-events: none;
	}

	.clear-button {
		margin-top: var(--space-medium);
		padding: var(--space-small) var(--space-medium);
		background-color: var(--color-surface);
		border: none;
		border-radius: var(--radius-medium);
		font: inherit;
		font-weight: bold;
		min-height: var(--tap-target-min);
		cursor: pointer;
		transition: background-color 0.2s;
	}
	@media (hover: hover) {
		.clear-button:hover {
			background-color: var(--color-muted);
		}
	}
	.clear-button:focus-visible {
		outline: 2px dashed var(--color-text);
		outline-offset: 2px;
	}

	.game-main {
		max-width: 70rem;
	}
	.game-heading {
		max-width: var(--content-width);
		margin: 0 auto;
	}

	.puzzle-and-clues-container {
		display: grid;
		grid-template-columns: 1fr;
		gap: var(--space-large);
		align-items: start;
	}

	.game-content {
		width: 100%;
		margin: 0 auto;
	}

	summary {
		cursor: pointer;
		padding: var(--space-small) var(--space-medium);
		background-color: var(--color-surface);
		border-radius: var(--radius-medium);
		font-weight: bold;
		transition: background-color 0.2s;
		width: fit-content;
		min-height: var(--tap-target-min);
	}
	@media (hover: hover) {
		summary:hover {
			background-color: var(--color-muted);
		}
	}
	summary:focus-visible {
		outline: 2px dashed var(--color-text);
		outline-offset: 2px;
	}

	@media (min-width: 48rem) {
		.game-content {
			width: fit-content;
		}
		.puzzle-and-clues-container {
			grid-template-columns: var(--puzzle-size) auto;
		}
	}
</style>
