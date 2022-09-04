<!-- TODO -->
<!-- 
Earth time
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
    <ul class="list-group">
      <li class="list-group-item" v-show="timestamp">
        <strong>Timestamp:</strong> {{ timestamp }}
      </li>
      <li class="list-group-item" v-show="date">
        <strong>Date:</strong> {{ date }}
      </li>
      <li class="list-group-item" v-show="time">
        <strong>Time:</strong> {{ time }}
      </li>
      <li class="list-group-item" v-show="year">
        <strong>Current Year:</strong> {{ year }}
      </li>
      <li class="list-group-item" v-show="fulldatetime">
        <strong>Full Date:</strong> {{ fulldatetime }}
      </li>
    </ul>
    <timeClock v-bind:test="date"/>
  </div>
  
  <messageTest v-bind:msg="message" />
  <input type="text" v-model="message" />
  <button v-on:click="alertMessage">Alert</button>
  
</template>

<script>
import messageTest from "./components/messageTest.vue";
import timeClock from "./components/timeClock.vue";

export default {
  name: "App",
  components: {
    messageTest,
    timeClock,
  },

  data: () => ({
    message: "We've got a city to burn.",
    date: "",
    time: "",
    year: "",
    timestamp: "",
    fulldatetime: "",
  }),

  methods: {
    alertMessage() {
      alert(this.message);
    },
    printDate: function () {
      return new Date().toLocaleDateString();
    },
    printTime: function () {
      return new Date().toLocaleTimeString();
    },
    printYear: function () {
      return new Date().getFullYear();
    },
    printTimestamp: function () {
      return Date.now();
    },
    printFullDate: function () {
      return new Date();
    },
    // zeroPadding: function (num, digit) {
    //   var zero = "";
    //   for (var i = 0; i < digit; i++) {
    //     zero += "0";
    //   }
    //   return (zero + num).slice(-digit);
    // },
    // updateTime: function () {
    //   var cd = new Date();
    //   this.clock.time =
    //     this.zeroPadding(cd.getHours(), 2) +
    //     ":" +
    //     this.zeroPadding(cd.getMinutes(), 2) +
    //     ":" +
    //     this.zeroPadding(cd.getSeconds(), 2);
    //   this.clock.date =
    //     this.zeroPadding(cd.getFullYear(), 4) +
    //     "-" +
    //     this.zeroPadding(cd.getMonth() + 1, 2) +
    //     "-" +
    //     this.zeroPadding(cd.getDate(), 2) +
    //     " " +
    //     this.week[cd.getDay()];
    // },
  },
  mounted: function () {
    this.date = this.printDate();
    this.time = this.printTime();
    this.timestamp = this.printTimestamp();
    this.year = this.printYear();
    this.fulldatetime = this.printFullDate();
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
ul {
  list-style-type: none; /* Remove bullets */
  padding: 500; /* Remove padding */
  margin: 200; /* Remove margins */
  text-align: left;
}
</style>
