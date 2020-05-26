<script>
    let running = false;
    let time = 0;
    let startTime;
    let newTime;
    let interval;

    function startTimer() {
        running = true
        startTime = new Date().getTime();
        interval = setInterval(getTime, 1000);
    }

    function stopTimer() {
        running = false;
        clearInterval(interval);
    }

    function resetTimer() {
        time = 0;
    }

    function getTime() {
        newTime = new Date().getTime();
        time = Math.floor((newTime - startTime)/1000)
    }
</script>

{#if !running}
    <button on:click={startTimer}>start</button>
    {#if time !== 0}
        <button on:click={resetTimer}>reset</button>
    {/if}
{:else}
    <button on:click={stopTimer}>stop</button>
{/if}

<div>
    <h1>
        {time}s
    </h1>
</div>

<style>
	h1 {
		color: #ff3e00;
		font-size: 8em;
		font-weight: 100;
	}
</style>