<script>
    import HowTo from './howTo.svelte';
    import Timer from './timer.svelte';

    let audio;

    function timerEnds(e)
    {
        audio.play();
        const value = e.detail.mensaje;
        console.log(value);
    }
</script>

<h1>Hand Washing App</h1>

<Timer on:end={timerEnds} />
<HowTo />

<h3>
  <a href="https://vid.alarabiya.net/images/2020/03/22/1ff220bb-03ef-4911-b8e1-32f72eed355e/1ff220bb-03ef-4911-b8e1-32f72eed355e.PNG">Picture source</a>
  <a href="https://english.alarabiya.net/en/coronavirus/2020/03/22/Coronavirus-Hand-washing-is-important-here-s-how-to-do-it-effectively">Sound source</a>
</h3>

<audio bind:this={audio}>
    <source src="sound.wav" />
</audio>


<style>
    h1, h3 {
        text-align: center
    }
</style>