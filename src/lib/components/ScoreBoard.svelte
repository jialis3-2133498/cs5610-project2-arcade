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
    }
    .score, .best-score {
        background-color: #9fd3c7;
        min-width: 100px;
        padding: 12px, 20px;
        border-radius: 8px;
        text-align: center;
    }
</style>