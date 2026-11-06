<script>
    let { value } = $props();
</script>

<div class="tile">
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
        background-color: #ececec;
        font-size: 24px;
        font-weight: bold;
        border-radius: 4px;
    }
</style>