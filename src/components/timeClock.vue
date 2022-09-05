<template>
    <div>{{ dateTime.day }}/{{ dateTime.month }}/{{ dateTime.year }}   {{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
    <div>{{ dateTime.day }}/{{ dateTime.month }}/{{ dateTime.year }}   {{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
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
          day :date.getDay(),
          month:date.getMonth()+1,
          year:date.getFullYear()
        },
        timer: undefined,
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
    },
    beforeMount() {
      this.timer = setInterval(this.setDateTime, 1000);
    },
    beforeUnmount() {
      clearInterval(this.timer);
    },
  };
  </script>