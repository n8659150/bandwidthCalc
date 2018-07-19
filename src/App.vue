<template>
  <div id="app">
    <img src="./assets/logo.png">
    <bandWidthCalc />
  </div>
</template>

<script>
import bandWidthCalc from './components/bandWidthCalc'

export default {
  name: 'App',
  components: {
    bandWidthCalc
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
