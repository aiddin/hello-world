<template>
  <div>
    <h2 class="text-center mb-3">Vue Get Full Date and Time Example</h2>
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
  </div>
  <img
    alt="Vue logo"
    src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/i/d1fb123f-8d74-47c7-9759-acc3c7681530/ddbbmtz-07697bd8-557d-4828-ae75-246d6a3adfb4.jpg"
    width="200"
    height="200"
  />
  <alienClock v-bind:msg="message" />
  <alienClock v-bind:time="0" />
  <alienClock v-bind:alienTime="0" />
  <input type="text" v-model="message" />
  <button v-on:click="alertMessage">Alert</button>
</template>

<script>
import alienClock from './components/alienClock.vue'

export default {
  name: 'App',
  components: {
   alienClock,
  },

        
        data: () => ({
          message: 'Hello World!',
          date: '',
          time: '',
          year: '',
          timestamp: '',
          fulldatetime: ''
        }),

        methods: {
          alertMessage(){
              alert(this.message)
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
          printFullDate: function(){
            return new Date();
          }
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
</style>
