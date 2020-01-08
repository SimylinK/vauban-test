<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ObjectDisplay v-bind:object="apiObject"/>
  </div>
</template>

<script>
import ObjectDisplay from './components/ObjectDisplay.vue'

export default {
  name: 'test',
  data() {
    return {
      apiObject: null,
    }
  },
  components: {
    ObjectDisplay
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
