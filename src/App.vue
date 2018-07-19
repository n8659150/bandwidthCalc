<template>
  <div id="app">
    <ribbon :profile="profile"></ribbon>
    <div>
      <img src="./assets/inspector.jpg" width="300" height="300">
      <bandWidthCalc />
    </div>
    <!-- <footer><a href="//www.jackyangli.com">2018  Jack Li©</a></footer> -->
  </div>
</template>

<script>
import ribbon from './components/ribbon'
import bandWidthCalc from './components/bandWidthCalc'

export default {
  name: 'App',
  data(){
    return {
      profile:'//github.com/n8659150/bandwidthCalc'
    }
  },
  components: {
    ribbon,
    bandWidthCalc
  }
}
</script>

<style>
html,body {
  margin:0;
  height:100%;
  display:flex;
  flex:1;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display:flex;
  flex:1;
  justify-content: center;
  align-items:center;
  /* margin-top: 60px; */
}
</style>
