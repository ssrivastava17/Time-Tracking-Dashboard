<script>
    export let time; // indicates that Activity takes text as prop
    export let timeframe;
    export let color;
    export let image;
     import work from '../assets/icon-work.svg';
     import play from '../assets/icon-play.svg';
     import study from '../assets/icon-study.svg';
     import exercise from '../assets/icon-exercise.svg';
     import social from '../assets/icon-social.svg';
     import self from '../assets/icon-self-care.svg';
    import ellipsis from '../assets/icon-ellipsis.svg';
    let images= [work, play, study, exercise, social, self];
    let thisWeek;
    let lastWeek;

    $: {
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
}

</script>

<!-- background-color:{color}; -->

<div class="background" style="background-color:{color}; background-image: url({images[image]});">

    <div class="card">
        <div class="title">{time.title} </div>
        <div class="current">{thisWeek}hrs </div>
        <div class="last">Last Week - {lastWeek}hrs </div>
    </div>

</div>

<style>
     @import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap');
     .card{
          border: 1px black;
          background-color: hsl(235, 46%, 20%);
          text-align: left;
          top: 50%;
          left: 50%;
          transform: translate(0%, 18%);
          border-radius: 15px;
          height: 80%;
          padding: 5% 0 0 10%;
          color: white;
          /* visibility: hidden; */
     }

     .title{
          font-size: 18px;
          padding: 10px 0;
          width: 100px;
     }

     .title::before{
          content: url(ellipsis);
          position: absolute;
          right: 100px; 
     }

     .current{
          font-family: 'Rubik', sans-serif;
          font-size: 40px;
          font-weight: 300;
          padding: 15px 0 5px 0;
     }

     .last{
          font-size: 12px;
          color: hsl(236, 100%, 87%);
     }

     .background{
          background-repeat: no-repeat;
          border-radius: 15px;
          background-position: 90% -3%;
          background-size: 25%;
     }
</style>