<template>
  <div id="app">
    <img src="./assets/logo.png">
    <alert :title="title" :text="text"></alert>
  </div>
</template>

<script>
import Alert from './components/Alert'

export default {
  data () {
    return {
      title: 'Vue Bootstrap Component',
      text: 'Isn\'t it easy?'
    }
  },
  name: 'App',
  components: {
    Alert
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
