<template>
  <div id="app">
    <h2>Line chart with data from server.</h2>
    <container/>
  </div>
</template>

<script>
import container from './components/container.vue'

export default {
  name: 'App',
  components: {
    container
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
