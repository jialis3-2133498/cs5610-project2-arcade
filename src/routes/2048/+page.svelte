<script>
    import GameBoard from "../../lib/components/GameBoard.svelte";
    import ScoreBoard from "../../lib/components/ScoreBoard.svelte";
    import { move, canMove, spawn } from "@jialisheng/arcade-core";

    let board = $state([
        [2, 0, 2, 0],
        [0, 4, 0, 0],
        [0, 0, 2, 0],
        [0, 0, 0, 0]
    ])
    let score = $state(0);
    let bestScore = $state(0);

    /**
    * @param {"left" | "right" | "up" | "down"} direction
    */
    function handleMove(direction) {
        if (!canMove(board, direction)) {
            return;
        }
        const newBoard = move(board, direction);
        const boardWithNewTile = spawn(newBoard);
        board = boardWithNewTile;
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
</script>
<svelte:window onkeydown={handleKeyDown} />



<h1>2048</h1>
<p>Welcome to my 2048 game!</p>

<ScoreBoard {score} {bestScore} />
<GameBoard {board} />
<div class="controls">
    <button onclick={() => handleMove("left")}>Left</button>
    <button onclick={() => handleMove("right")}>Right</button>
    <button onclick={() => handleMove("up")}>Up</button>
    <button onclick={() => handleMove("down")}>Down</button>
</div>

