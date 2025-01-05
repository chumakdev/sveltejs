<script>
    import { onMount } from 'svelte';
    import { writable } from 'svelte/store';

    export let timerData = writable('');
  
    function calculateTimeLeft() {
      const getNowTime = new Date();
      const getTimerMidnight = new Date();
      getTimerMidnight.setHours(24, 0, 0, 0);
  
      const diff = getTimerMidnight - getNowTime;
  
      const timerDays = Math.floor(diff / (1000 * 60 * 60 * 24));
      const timerHours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const timerMinutes = Math.floor((diff / (1000 * 60)) % 60);
      const timerSeconds = Math.floor((diff / 1000) % 60);
  
      return `${timerDays}d ${timerHours}h ${timerMinutes}m ${timerSeconds}s`;
    }
  
    let interval;
  
    onMount(() => {
      timerData.set(calculateTimeLeft());
  
      interval = setInterval(() => {
        timerData.set(calculateTimeLeft());
      }, 1000);
  
      return () => clearInterval(interval);
    });
  </script>
  
  <div class="popup-content__timer-value">
    {#await $timerData then time}
      {time}
    {/await}
  </div>
  

  <style>
    .popup-content__timer-value {
      font-size: 26px;
      font-family: "Fira Sans", serif;
      font-style: normal;
      font-weight: 600;
      line-height: normal;
      color: #828896;
	}

  @media screen and (max-width: 650px) {
    .popup-content__timer-value {
      font-size: 17px;
    }
  }
  </style>