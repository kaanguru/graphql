<template>
  <div id="app">
    <Launches />
  </div>
</template>

<script>
import Launches from './components/Launches.vue'

export default {
  name: 'app',
  components: {
    Launches
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&family=Space+Grotesk&display=swap');

html {
  background-color: #FFFDE3;
  @apply bg-gradient-to-r from-emerald-200;
}

#app {
  font-family: 'Space Grotesk', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
