<template>
  <div>
    {{ clock.day }}/{{ clock.month }}/{{ clock.year }} {{ clock.hours }}:{{
      clock.minutes
    }}:{{ clock.seconds }}
  </div>
</template>
<script>

export default {
  name: "App",
  data() {
    return {
    //   Clock: {
    //     alienepoch: clock.convertAlien(),
    //     hours: this.minutes,
    //     minutes: clock.getMinutes(),
    //     seconds: clock.getSeconds(),
    //     day: clock.getDate(),
    //     month: clock.getMonth() + 1,
    //     year: clock.getFullYear(),
    //   },
    };
  },

  methods: {
    Clock: function () {
      Clock = this;
      //  var timeout;
      //  var time;
      convertAlien();
      var alienesec = Math.trunc(alienepoch / 1000);
      var temp = alienesec % 90;
      var tempmin = Math.trunc(alienepoch / 90);
      var realmin = tempmin % 90;
      var temphour = Math.trunc(tempmin / 90);
      var realhour = temphour % 36;
      var tempday = Math.trunc(temphour / 36);
      var tempyear = Math.trunc(tempday / 770); //need fixing base epoch
      var realday = tempday % 770;
      var viewday;
      var realmonth;

      if (realday <= 44) {
        realmonth = "1";
        viewday = realday;
      }
      if (realday <= 86 && realday > 44) {
        realmonth = "2";
        viewday = realday - 44;
      }
      if (realday > 86 && realday <= 134) {
        realmonth = "3";
        viewday = realday - 86;
      }
      if (realday > 134 && realday <= 174) {
        realmonth = "4";
        viewday = realday - 174;
      }
      if (realday <= 222 && realday > 175) {
        realmonth = "5";
        viewday = realday - 175;
      }
      if (realday <= 266 && realday > 222) {
        realmonth = "6";
        viewday = realday - 222;
      }
      if (realday <= 366 && realday > 306) {
        realmonth = "7";
        viewday = realday - 306;
      }
      if (realday <= 350 && realday > 306) {
        realmonth = "8";
        viewday = realday - 306;
      }
      if (realday <= 393 && realday > 350) {
        realmonth = "9";
        viewday = realday - 350;
      }
      if (realday <= 432 && realday > 393) {
        realmonth = "10";
        viewday = realday - 393;
      }
      if (realday <= 472 && realday > 432) {
        realmonth = "11";
        viewday = realday - 432;
      }
      if (realday <= 514 && realday > 472) {
        realmonth = "12";
        viewday = realday - 472;
      }
      if (realday <= 558 && realday > 514) {
        realmonth = "13";
        viewday = realday - 514;
      }
      if (realday <= 606 && realday > 558) {
        realmonth = "14";
        viewday = realday - 558;
      }
      if (realday <= 648 && realday > 606) {
        realmonth = "15";
        viewday = realday - 606;
      }
      if (realday <= 688 && realday > 648) {
        realmonth = "16";
        viewday = realday - 648;
      }
      if (realday <= 732 && realday > 688) {
        realmonth = "17";
        viewday = realday - 688;
      }
      if (realday <= 770 && realday > 732) {
        realmonth = "18";
        viewday = realday - 732;
      }

      month = realmonth;
      year = tempyear;
      day = viewday;
      hours = realhour;
      minutes = realmin;
      seconds = temp;
      this.start = start;
    },
    convertAlien: function () {
      const d1 = new Date();
      var test = d1.getTime();
      // 1.13764038050463 = millis diff between
      var alienepoch = test * 1.13764038050463;
      return alienepoch;
    },
    start: function () {
      timeout = setInterval(tick, 0);
      time = Date.now();
      convertToAlien();
      console.log("Alien Time since UNIX epoch :" + alienepoch);
    },
    display: function () {
      var hours = clock.hours;
      var minutes = clock.minutes;
      var seconds = clock.seconds;
      var viewday = clock.day;
      var month = clock.month;
      var year = clock.year;
      //add zero
      hours = hours < 10 ? "0" + hours : "" + hours;
      minutes = minutes < 10 ? "0" + minutes : "" + minutes;
      seconds = seconds < 10 ? "0" + seconds : "" + seconds;
      convertToAlien();
      document.getElementById("pickedalien").innerHTML =
        "Picked alien time is   Year: " +
        year +
        " Month : " +
        month +
        " Day :" +
        viewday +
        "\tTime :" +
        hours +
        ":" +
        minutes +
        ":" +
        seconds;

      // console.log("Alien time is   Year: "+year+ " Month : "+month +" Day :"+viewday +"\ttime :"+hours + ":" + minutes + ":" + seconds);
    },
    update: function () {
      var seconds = (clock.seconds += 1);

      if (seconds === 90) {
        clock.seconds = 0;
        var minutes = ++clock.minutes;

        if (minutes === 90) {
          clock.minutes = 0;
          var hours = ++clock.hours;

          if (hours === 36) clock.hours = 0;
          var day = ++clock.day;

          if (day === 770) clock.day = 1;
          var year = ++clock.year;
          return year;
        }
      }
    },
    tick: function () {
      time += 500;
      timeout = setTimeout(tick, time - Date.now());
      display();
      update();
    },
  },
};
</script>
