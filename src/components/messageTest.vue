<template>
  <div class="test">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>

export default {
  name: 'messageTest',
  props: {
    msg: String,
    
  }
}
</script>

