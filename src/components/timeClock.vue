<template>
    <div>{{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
  </template>
  <script>
  const date = new Date();
  export default {
    name: "App",
    data() {
      return {
        dateTime: {
          hours: date.getHours(),
          minutes: date.getMinutes(),
          seconds: date.getSeconds(),
        },
        
      };
    },
    methods: {
      setDateTime() {
        const date = new Date();
        this.dateTime = {
          hours: date.getHours(),
          minutes: date.getMinutes(),
          seconds: date.getSeconds(),
        };
      },
    },
    beforeMount() {
      
      this.timer = setInterval(this.setDateTime, 500);
    },
    beforeUnmount(){
      clearInterval(this.timer);
    }
  };
  </script>