<template>
    <div>{{ dateTime.day }}/{{ dateTime.month }}/{{ dateTime.year }}   {{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
    <div>{{ dateTime.day }}/{{ dateTime.month }}/{{ dateTime.year }}   {{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
  </template>
  <script>
  const date = new Date();
  var time;
  export default {
    name: "App",
    data() {
      //return = return data(display?)
      return {
        //earth date time
        dateTime: {
          hours: date.getHours(),
          minutes: date.getMinutes(),
          seconds: date.getSeconds(),
          day: date.getDate(),
          month:date.getMonth()+1,
          year:date.getFullYear()
        },
        alienDate:{

        },
        clock:{
          hours: date.getHours(),
          minutes: date.getMinutes(),
          seconds: date.getSeconds(),
          day: date.getDate(),
          month:date.getMonth()+1,
          year:date.getFullYear()
        }
        
      };
    },
    methods: {
      setDateTime() {
        const date = new Date();
        this.dateTime = {
          hours: date.getHours(),
          minutes: date.getMinutes(),
          seconds: date.getSeconds(),
          day: date.getDate(),
          month:date.getMonth()+1,
          year:date.getFullYear()
        };
      },
      Clock(){
      var clock = this, timeout, time;
      this.convertAlien();
      
       },
       convertAlien(){
        const d1 = new Date();
        var test = d1.getTime();
        // 1.13764038050463 = millis diff between
        var alienepoch=((test*1.13764038050463));
        return alienepoch;
       }
      // display(){
      //    var = clock.hours;

      // },
      // tick(){
      //   time += 500;
      //   timeout = setTimeout(tick, time - Date.now());
      // }
    },
    beforeMount() {
      //set refresh
     time += 1000;
      this.timer = setInterval(this.setDateTime,time-Date.now());
    },
    beforeUnmount(){
      clearInterval(this.timer);
    }
  }


  </script>