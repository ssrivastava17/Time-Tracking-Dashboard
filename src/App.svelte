<script>
  import logo from './assets/svelte.png'
  import Counter from './lib/Counter.svelte'
  import Activity from './lib/Activity.svelte';
  import timeData from '../data.json';
  import {writable} from 'svelte/store';

  

  let myTimeframe ="Weekly";
  const whatever = writable(myTimeframe);

  function updateDaily(){
    $whatever = "Daily";
    console.log("Daily");
  }

  function updateWeekly(){
    $whatever = "Weekly";
    console.log("Weekly");
  }

  function updateMonthly(){
    $whatever = "Monthly";
    console.log("Monthly");
  }

</script>

<main>
  <button on:click={updateDaily}>Daily</button>
  <button on:click={updateWeekly}>Weekly</button>
  <button on:click={updateMonthly}>Monthly</button>

  <!-- <Activity title="Work" thisWeek={timeData[0].timeframes.daily.current} lastWeek=5/> -->
  {#each timeData as myTime}
    <Activity time={myTime} timeframe={whatever} />
  {/each}

  <!-- <p>
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p> -->
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
