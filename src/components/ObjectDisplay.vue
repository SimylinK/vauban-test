<template>
  <table id="object">
    <tr
      v-for="(value, name) in object"
      :key="name"
    >
      <td id="name"> {{ name }} </td>
      <td id="value">
        <ValueDisplay v-bind:value="value" @clicked="onClickChild"/>
      </td>
    </tr>
  </table>
</template>

<script>
import ValueDisplay from './ValueDisplay.vue'

export default {
  name: 'ObjectDisplay',
  props: {
    object: Object
  },
  components: {
    ValueDisplay
  },
  methods: {
    onClickChild(data) {
      alert('TEST');
      this.$emit('clicked', data);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#object {
  border: solid black;
  width:60%;
  margin-left:auto;
  margin-right:auto;
  border-collapse: collapse;
}

#object tr td {
  border: 2px solid gray;
}

</style>
