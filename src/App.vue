<!-- TODO -->
<!-- 
  Earth date
Earth datetime conversion
Alien date&time
Alien datetime conversion

-->


<template>
  
  <div>
    <h1 class="text-center">Alien Clock</h1>
    <img
    alt="Vue logo"
    src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/i/d1fb123f-8d74-47c7-9759-acc3c7681530/ddbbmtz-07697bd8-557d-4828-ae75-246d6a3adfb4.jpg"
    width="200"
    height="200"
  />
    
    <timeClock v-bind:test="date"/>
  </div>
  
  <messageTest v-bind:msg="message" />
  <input type="text" v-model="message" />
  <button v-on:click="alertMessage">Alert</button>
  <timeSecondConvert/>
  <timerClock />
  <!-- <alienClock/> -->
</template>

<script>
import messageTest from "./components/messageTest.vue";
import timeClock from "./components/timeClock.vue";
import timeSecondConvert from "./components/timeSecondConvert.vue";
// import alienClock from "./components/alienClock.vue";
import timerClock from "./components/timerClock.vue";
export default {
  name: "App",
  components: {
    messageTest,
    timeClock,
    timeSecondConvert,
    // alienClock
    timerClock
  },
  // fetch data
  data: () => ({
    message: "We've got a city to burn.",
   
  }),
// functions and method
  methods: {
    alertMessage() {
      alert(this.message);
    },
   
   
  },

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: maroon;

  background: black;
  background-size: cover;
}

</style>
