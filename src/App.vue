<template>
  <div id="app">
   <SimonTheGame />
  </div>
</template>

<script>
import SimonTheGame from './components/SimonTheGame.vue'

export default {
  name: 'App',
  components: {
    SimonTheGame
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}

</style>
