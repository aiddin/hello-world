<template>
    <!-- <div>
        {{ dispay.month }}/{{ clock.month }}/{{ clock.year }} {{ clock.hours }}:{{
                clock.minutes
        }}:{{ clock.seconds }}
        <div class="texxt" id="pickedalien"></div>
    
    </div> -->
    <div>{{ clock.day }}/{{ dateTime.month }}/{{ dateTime.year }}   {{ dateTime.hours }}:{{ dateTime.minutes }}:{{ dateTime.seconds }}</div>
</template>

<script>

var realhour;
var realmin;
var temp;
var viewday;
var realmonth;
var tempyear;
// var clock = new Clock();
// clock.start();
// var test ;
// const d1 = new Date.now();
// test= d1*1.13764038050463;
export default {
    name: "App",
    data(){

    

        return {
            clock: {
            hours: realhour,
          minutes: realmin,
          seconds: temp,
          day: viewday,
          month:realmonth,
          year:tempyear

        },
            // time: 500,
            // timeout: setTimeout(tick(), time - Date.now()),
            //  alienEpoch: '',

            //   Clock: {
            //     alienEpoch: this.convertAlien(),
            //     hours: this.minutes,
            //     minutes: clock.getMinutes(),
            //     seconds: clock.getSeconds(),
            //     day: clock.getDate(),
            //     month: clock.getMonth() + 1,
            //     year: clock.getFullYear(),
            //   },
        };
    },

    mounted(){
      
    },
    computed: {
      

        // convertAlien() {
        //     const d1 = new Date();
        //     var test = d1.getTime();
        //     // 1.13764038050463 = millis diff between
        //    this.alienEpoch = test * 1.13764038050463;
        //     return this.alienEpoch;
        // },
    },
    methods: {
        clockTest() {
           var clock=this;
            //  var timeout;
            //  var time;
            clock.convertToAlien();
            var alienesec = Math.trunc( this.alienepoch/ 1000);
             temp = alienesec % 90;
            var tempmin = Math.trunc(clock.alienepoch / 90);
             realmin = tempmin % 90;
            var temphour = Math.trunc(tempmin / 90);
             realhour = temphour % 36;
            var tempday = Math.trunc(temphour / 36);
             tempyear = Math.trunc(tempday / 770); //need fixing base epoch
            var realday = tempday % 770;
             viewday;
             realmonth;

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
            this.update();
            this.display();
            this.month = realmonth;
            clock.year = tempyear;
            clock.day = viewday;
            clock.hours = realhour;
            clock.minutes = realmin;
            clock.seconds = temp;
            
        
        // this.clock.start = this.start();
        },
        convertToAlien(){
        const d1 = new Date.now();

        var test = d1.getTime();
        // 1.13764038050463 = millis diff between
        var alienepoch=((test*1.1376));
        return alienepoch;
        
    },

        start() {
            this.timeout = setInterval(this.tick, 0);
            this.time = Date.now();
            this.convertToAlien();
            console.log("Alien Time since UNIX epoch :" + global.alienEpoch);
        },
        display() {

            var hours = this.clock.hours;
            var minutes = this.clock.minutes;
            var seconds = this.clock.seconds;
            var viewday = this.clock.day;
            var month = this.dateTime.month;
            var year = this.clock.year;
            //add zero
            hours = hours < 10 ? "0" + hours : "" + hours;
            minutes = minutes < 10 ? "0" + minutes : "" + minutes;
            seconds = seconds < 10 ? "0" + seconds : "" + seconds;
            this.convertToAlien();
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
        update() {
            var seconds = (this.clock.seconds += 1);

            if (seconds === 90) {
                this.clock.seconds = 0;
                var minutes = ++this.clock.minutes;

                if (minutes === 90) {
                    this.clock.minutes = 0;
                    var hours = ++this.clock.hours;

                    if (hours === 36) this.clock.hours = 0;
                    var day = ++this.clock.day;

                    if (day === 770) this.clock.day = 1;
                    
                    var year = ++this.clock.year;
                    
                   
                }
            }
        },
        tick(){
            var tick = this.tick;
            var time = 500;
            // eslint-disable-next-line
            var timeout = setTimeout(tick, time - Date.now());
            this.display();
            this.update();
        },
    },
};
</script>
<style scoped>
.texxt {
    text-align: center;
    font-family: Verdana;
    font-size: 1em;
    padding: 0.7em;
    color: white;
}
</style>