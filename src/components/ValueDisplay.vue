<template>
  <div id="valueDisplay">

    <!-- For a list of URIs -->
    <div v-if="Array.isArray(value)">
      <ul id="value-list">
        <li
          v-for="element in value"
          :key="element"
        >
          <p v-on:click="apiCall(element, displayObject);"> {{ element }} </p>
        </li>
      </ul>
    </div>

    <!-- For a simple URI -->
    <div v-else-if="value.match(/https:\/\/*\//)">
      <p v-on:click="apiCall(value, displayObject);"> {{ value }} </p>
    </div>

    <!-- For the strings -->
    <div v-else>
      {{ value }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ValueDisplay',
  props: {
    value: [String, Array]
  },
  methods: {
    displayObject(data) {
      this.$emit('clicked', data);
    },
    apiCall(url, callback) {
      // Create a request variable and assign a new XMLHttpRequest object to it.
      var request = new XMLHttpRequest();

      // Open a new connection, using the GET request on the URL endpoint
      request.open('GET', url, true);

      request.onload = function() {
        var data = JSON.parse(this.response);
        callback(data);
      }

      // Send request
      request.send();
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#valueDisplay ul {
  list-style: none;
}

#valueDisplay p {
  color:blue;
  cursor: pointer;
}

</style>
