<template>
  <div id="app">
    <card></card>
  </div>
</template>

<script>
import card from './components/cards'

export default {
  name: 'app',
  components: {
    card
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
