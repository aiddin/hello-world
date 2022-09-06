<template lang="html">
  <div v-if="isEnded">
    Ended.
  </div>

  <div v-else>
    <div>Days: {{ days }}</div>
    <div>Hours: {{ hours }}</div>
    <div>Minutes: {{ minutes }}</div>
    <div>Seconds: {{ seconds }}</div>
  </div>
</template>

<script>
export default {
  props: {
    endDate: {
      type: Date // Date.parse(this.endDate)
    }
  },
  data () { 
    return {
      days: null,
      hours: null,
      minutes: null,
      seconds: null,
      isEnded: null
    }
  },
  methods: {
    updateRemaining (distance) {
      this.days = Math.floor(distance / (1000 * 60 * 60 * 24))
      this.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
      this.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))
      this.seconds = Math.floor((distance % (1000 * 60)) / 1000)
    },
    
    tick () {
      const currentTime = new Date()
      const distance = Math.max(this.endDate - currentTime, 0)
      this.updateRemaining(distance)
      
      if (distance === 0) {
        clearInterval(this.timer)
        this.isEnded = true
      }
    }
  },
  
  mounted () {
    this.tick()
    this.timer = setInterval(this.tick.bind(this), 1000)
  },
  
  destroy () {
    clearInterval(this.timer)
  }
}
</script>