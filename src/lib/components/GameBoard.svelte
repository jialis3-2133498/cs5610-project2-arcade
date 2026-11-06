<script>
    import Tile from "./Tile.svelte";
    let { board } = $props();
</script>

<div class="board">
    {#each board as row, rowIndex (rowIndex)}
        {#each row as value, colIndex (`${rowIndex}-${colIndex}`)}
                <Tile {value} />
        {/each}
    {/each}
</div>

<style>
    .board {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 8px;
        width: min(90vw, 400px);
        padding: 8px;
        background-color: #9fd3c7;
        border-radius: 8px;
    }
</style>