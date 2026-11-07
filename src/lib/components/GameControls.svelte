<script>
    /** @type {{ onNewGame: () => void }} */
    let { onNewGame } = $props();
</script>

<button onclick={onNewGame}>New Game</button>