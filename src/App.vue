<template>
  <div id="app">
    <div class="row">
      <div class="sidebar col-md-4 col-xs-4"></div>
      <div class="content col-md-8 col-xs-8">
        <cards></cards>
      </div>
    </div>
  </div>
</template>

<script>
import cards from './components/cards'

export default {
  name: 'app',
  components: {
    cards
  }
}
</script>

<style>
body{
margin: 0;
height: 100vh;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
}

#app{
  height: 100vh;
}

.sidebar{
  background-color: #4A354E;
  height: 100vh;
}

.content{
  margin: 0;
  padding: 0;
  overflow-y:scroll;
  height: 100vh
}
</style>
