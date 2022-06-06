<script>
    export let time; // indicates that Activity takes text as prop
    export let timeframe;
    let thisWeek;
    let lastWeek;

   if(timeframe == "Daily"){
        thisWeek = time.timeframes.daily.current;
        lastWeek = time.timeframes.daily.previous;
   } else if (timeframe == "Weekly"){
        thisWeek = time.timeframes.weekly.current;
        lastWeek = time.timeframes.weekly.previous;
   } else{
        thisWeek = time.timeframes.monthly.current;
        lastWeek = time.timeframes.monthly.previous;
   }

</script>

<div class="background">

    <div class="card">
        <p>{time.title} </p>
        <p>{thisWeek}hrs </p>
        <p>Last Week - {lastWeek}hrs </p>
    </div>

</div>