<script>
    /** @type {{ onNewGame: () => void }} */
    let { onNewGame } = $props();
</script>

<button onclick={onNewGame}>New Game</button>

<style>
    button {
        margin-top: 1rem;
        padding: 0.75rem 1.25rem;
        min-height: 44px;

        background-color: #427d6b;
        color: white;

        border: none;
        border-radius: 8px;

        font: inherit;
        font-weight: bold;
        cursor: pointer;
    }

    button:hover {
        background-color: #326454;
    }

    button:focus-visible {
        outline: 3px solid #2258bf;
        outline-offset: 3px;
    }
</style>