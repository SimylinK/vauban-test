<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AllCharacters/>
  </div>
</template>

<script>
import AllCharacters from './components/AllCharacters.vue'

export default {
  name: 'app',
  data() {
    return {
      people: null,
    }
  },
  components: {
    AllCharacters
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
