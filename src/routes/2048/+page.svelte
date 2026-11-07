<script>
    import GameBoard from "../../lib/components/GameBoard.svelte";
    import ScoreBoard from "../../lib/components/ScoreBoard.svelte";
    import { moveWithScore, canMove, hasMoves, spawn } from "@jialisheng/arcade-core";
    import { fade, scale } from "svelte/transition";
    import { onMount } from "svelte";
    import { gameStats } from "../../lib/state/gameStats.svelte.js";
    import GameControls from "../../lib/components/GameControls.svelte";

    let board = $state(createInitialBoard());
    let score = $state(0);
    let hasWon = $state(false);
    let keepPlaying = $state(false);
    let isGameOver = $derived(!hasMoves(board));

    onMount(() => {
        const savedBestScore = localStorage.getItem("bestScore");

        if (savedBestScore !== null) {
            const parsedScore = Number(savedBestScore);
            if (Number.isFinite(parsedScore) && parsedScore >= 0) {
                gameStats.bestScore = parsedScore;
            }
        }
    });

    /**
    * @param {"left" | "right" | "up" | "down"} direction
    */
    function handleMove(direction) {
        if (isGameOver || (hasWon && !keepPlaying)) {
            return;
        }
        if (!canMove(board, direction)) {
            return;
        }
        const newBoardObject = moveWithScore(board, direction);

        score += newBoardObject.score;
        if (score > gameStats.bestScore) {
            gameStats.bestScore = score;
            localStorage.setItem("bestScore", String(gameStats.bestScore));
        }

        if (!hasWon && checkWin(newBoardObject.board)) {
            hasWon = true;
        }

        board = spawn(newBoardObject.board);
    }

    /**
    * @param {KeyboardEvent} event
    */
    function handleKeyDown(event) {
        switch(event.key) {
            case "ArrowLeft":
                event.preventDefault();
                handleMove("left");
                break;
            case "ArrowRight":
                event.preventDefault();
                handleMove("right");
                break;
            case "ArrowUp":
                event.preventDefault();
                handleMove("up");
                break;
            case "ArrowDown":
                event.preventDefault();
                handleMove("down");
                break;
        }
    }

    function createEmptyBoard() {
        return Array.from({ length: 4 }, () => [0, 0, 0, 0]);
    }

    function createInitialBoard() {
        const emptyBoard = createEmptyBoard();
        const boardWithOneTile = spawn(emptyBoard);
        const boardWithTwoTiles = spawn(boardWithOneTile);

        return boardWithTwoTiles;
    }

    function newGame() {
        board = createInitialBoard();
        score = 0;
        hasWon = false;
        keepPlaying = false;
    }

    /**
    * @param {number[][]} board
    * @returns {boolean}
    */
    function checkWin(board) {
        if (board.flat().some(value => value >= 2048)) {
            return true;
        } else {
            return false;
        }
    }
</script>
<svelte:window onkeydown={handleKeyDown} />



<h1>2048</h1>

<p>Welcome to my 2048 game!</p>

<ScoreBoard {score} bestScore={gameStats.bestScore} />

<div class = "game-container">
    <GameBoard {board} />
    <div class="sr-only" role="status" aria-live="polite">
        {#if isGameOver}
            Game Over! No more moves available.
        {:else if hasWon && !keepPlaying}
            Congratulations! You reached 2048!
        {/if}
    </div>

    {#if isGameOver}
        <div class="game-overlay" transition:fade={{ duration: 300 }}>
            <h2>Game Over!</h2>
            <p>No more moves available.</p>
            <button onclick={newGame}>Try Again</button>
        </div>
        {:else if hasWon && !keepPlaying}
            <div class="game-overlay" transition:fade={{ duration: 300 }}>
                <div transition:scale={{ duration: 350, start: 0.8 }}>
                    <h2>Congratulations! You win!</h2>
                    <p>You reached 2048!</p>
                    <button onclick={() => keepPlaying = true}>
                        Continue Playing
                    </button>
                </div>
            </div>
    {/if}
</div>

<GameControls onNewGame={newGame} />


<div class="controls" role="group" aria-label="Game movement controls">
    <button class="up" aria-label="Move up" onclick={() => handleMove("up")}>↑</button>
    <button class="left" aria-label="Move left" onclick={() => handleMove("left")}>←</button>
    <button class="down" aria-label="Move down" onclick={() => handleMove("down")}>↓</button>
    <button class="right" aria-label="Move right" onclick={() => handleMove("right")}>→</button>
</div>

<style>
    .game-container {
        position: relative;
        width: min(90vw, 400px);
    }

    .game-overlay {
        position: absolute;
        inset: 0;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        background-color: rgba(255, 250, 235, 0.88);
        border-radius: 8px;
        text-align: center;
        padding: 16px;
        box-sizing: border-box;
        z-index: 1;
    }

    .game-overlay h2 {
        font-size: 2rem;
        margin-bottom: 8px;
    }

    .game-overlay button {
        padding: 10px 18px;
        border: none;
        border-radius: 6px;
        background-color: #427d6b;
        color: white;
        cursor: pointer;
    }

    .game-overlay button:focus-visible {
        outline: 3px solid #2258bf;
        outline-offset: 3px;
    }
    
    .sr-only {
        position: absolute;
        width: 1px;
        height: 1px;
        padding: 0;
        margin: -1px;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        white-space: nowrap;
        border: 0;
    }

    .controls {
        display: grid;
        grid-template-columns: repeat(3, 56px);
        grid-template-rows: repeat(2, 56px);
        gap: 8px;
        justify-content: center;
        margin-top: 16px;
    }

    .controls button {
        width: 56px;
        height: 56px;
        border: none;
        border-radius: 8px;
        background-color: #427d6b;
        color: white;
        font-size: 1.5rem;
        cursor: pointer;
        touch-action: manipulation;
    }

    .controls button:focus-visible {
        outline: 3px solid #2258bf;
        outline-offset: 3px;
    }

    .up {
        grid-column: 2;
        grid-row: 1;
    }

    .left {
        grid-column: 1;
        grid-row: 2;
    }

    .down {
        grid-column: 2;
        grid-row: 2;
    }

    .right {
        grid-column: 3;
        grid-row: 2;
    }

    @media (min-width: 768px) {
        .controls {
            display: none;
        }
    }
</style>

