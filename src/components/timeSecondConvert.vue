<template>
    <div id="app">
      <label for="timeInSeconds" class="np-label">Enter time in seconds</label>
      <input
        type="number"
        v-model="timeDurationInSeconds"
        id="timeInSeconds"
        class="np-input"
      />
      <div class="np-duration" v-if="timeDurationInSeconds">
        That's roughly {{ getTimeInHoursAndMins(timeDurationInSeconds) }}
      
    </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "App",
    data() {
      return {
        timeDurationInSeconds: 0,
        hoursText: "hrs",
        minsText: "mins",
      };
    },
    methods: {
      getTimeInHoursAndMins(timeInsSeconds) {
        if (timeInsSeconds && timeInsSeconds > 0) {
          const minsTemp = timeInsSeconds / 60;
          let hours = Math.floor(minsTemp / 60);
          const mins = minsTemp % 60;
  
          if (hours !== 0 && mins !== 0) {
            if (mins >= 59) {
              hours += 1;
              return +`${hours} ${this.hoursText} `;
            } else {
              return `${hours} ${this.hoursText} ${mins.toFixed(0)} ${
                this.minsText
              }`;
            }
          } else if (hours === 0 && mins !== 0) {
            return `${mins.toFixed(0)} ${this.minsText}`;
          } else if (hours !== 0 && mins === 0) {
            return `${hours} ${this.hoursText}`;
          }
        } else {
          return "-";
        }
      },
    },
  };
  </script>
  
  <style>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 20px;
    padding: 12px;
  }
  .np-label {
    color: #4b4b4b;
  }
  .np-input {
    font-size: 20px;
    margin: 12px 0;
    margin-left: 12px;
    border: 0px;
    background: #eee;
    padding: 4px 6px;
    outline: none;
  }
  .np-duration {
    margin-top: 10px;
    font-size: 26px;
  }
  .np-ft {
    margin-top: 10px;
  }
  </style>
  