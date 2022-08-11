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
html {

  background-color: beige;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
