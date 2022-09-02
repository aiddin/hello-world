<template>
  <div class="test">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>

export default {
  name: 'alienClock',
  props: {
    msg: String,
    time: Number,
    alienTime: Number
  }
}
</script>

