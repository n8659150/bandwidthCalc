<template>
  <div id="app">
    <ribbon :profile="profile"></ribbon>
    <img src="./assets/inspector.jpg">
    <bandWidthCalc />
    <footer><a href="//www.jackyangli.com">2018  Jack Li©</a></footer>
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
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
footer {
  position:absolute;
  bottom:3px;
  width:100vw;
}
footer a {
  font-size:14px;
  color:#2c3e50;
  text-decoration: none;
}
</style>
