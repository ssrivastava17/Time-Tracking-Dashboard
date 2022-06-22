<script>
  import Activity from './lib/Activity.svelte';
  import timeData from '../data.json';
  import headshot from './assets/image-jeremy.png';

 
  let myTimeframe = "Weekly";
  let colors = ["hsl(15, 100%, 70%)", "hsl(195, 74%, 62%)", "hsl(348, 100%, 68%)", "hsl(145, 58%, 55%)", "hsl(264, 64%, 52%)", "hsl(43, 84%, 65%)"]


  function updateDaily(){
    myTimeframe = "Daily";
    console.log("Daily");
  }

  function updateWeekly(){
    myTimeframe = "Weekly";
    // $whatever = "Weekly";
    console.log("Weekly");
  }

  function updateMonthly(){
    myTimeframe = "Monthly";
    // $whatever = "Monthly";
    console.log("Monthly");
  }

</script>

<body style="margin: 0;">
  <div class="wrapper">
    <div class="infoCard">
      <div class="info">
          <img src={headshot} alt="headshot of Jeremy">
          <p>Report for</p>
          <p class="name">Jeremy</p>
          <p class="name">Robson</p>
      </div>
      
      <button on:click={updateDaily}>Daily</button>
      <button on:click={updateWeekly}>Weekly</button>
      <button on:click={updateMonthly}>Monthly</button>

    </div>
    {#each timeData as myTime, i}
      <Activity time={myTime} timeframe={myTimeframe} color={colors[i]} image={i}/>
     
    {/each}
  </div>
  <div class="attribution">
    Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
    Coded by <a href="https://github.com/ssrivastava17">Stephanie Srivastava</a>.
  </div>
</body>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap');
  
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  button{
    color: white;
    border: none;
    background-color: transparent;
    font-family: 'Rubik', sans-serif;
    padding-left: 10%;
    padding-top: 5%;
    display: block;
  }

  .wrapper{
    display: grid;
    width: 825px;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 190px 180px;
    margin: auto;
    padding: 100px 10px;
    column-gap: 20px;
    row-gap: 20px;
  }

  .infoCard{
    background-color: hsl(235, 46%, 20%);
    color: white;
    font-family: 'Rubik', sans-serif;
    width: 200px;
    border-radius: 25px;
    grid-column-start: 1;
    grid-row-start: 1;
    grid-row-end: 3;
    text-align: left;
  }

  .info{
    background-color: hsl(246, 80%, 60%);
    border-radius: 25px;
    padding: 10%;
  }

  body{
    text-align: center;
    align-items: center;
    background-color: hsl(226, 43%, 10%);
    overflow: hidden;
    width: 100vw;
    height: 100vh;
  }

  body::before{
    height: 100%;
    width: 100vw;
    left: 50%;
    top:0;
    transform: translateX(-50%); 
    background: yellowgreen;
  }

  img {
    height: 5rem;
    width: 5rem;
    border: 5px solid white;
    border-radius: 50%;
  
  }

  .attribution{
    color: white;
  }
  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }



</style>
