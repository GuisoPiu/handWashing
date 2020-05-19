<script>
  import { createEventDispatcher } from 'svelte';
  import ProgressBar from './progressBar.svelte';
  let isRunning = false;

  $: progress = (totalSeconds - secondsLeft)/totalSeconds * 100;

  const totalSeconds = 3;
  let secondsLeft = totalSeconds;

  const dispatch = createEventDispatcher();

  function startTimer() {
    const timer= setInterval(() => {
      isRunning = true;
      secondsLeft -= 1;
      
      if(secondsLeft == -1) {
        clearInterval(timer);
        secondsLeft = totalSeconds;
        isRunning = false;
        dispatch('end', {
          mensaje:'Hola'
        });
      }
  }, 1000)
  }


</script>

<style>
    h2 {
        margin: 0;
    }

    .start {
        background: rgb(175, 73, 73);
        width: 100%;
        margin: 10px 0;
    }

    .start[disabled] {
      background-color: rgb(194, 194, 194);
      cursor: not-allowed;
    }
</style>

<div bp='grid'>
    <h2 bp="offset-5@md 4@md @12sm">
      Seconds Left: {secondsLeft}
    </h2>
</div>

<ProgressBar {progress} />
<div bp="grid">
  <button disabled={isRunning} on:click={startTimer} bp="offset-5@md 4@md @12sm" class="start" >Start</button>
</div>