<template>
  <div id="characters">
    <select @change="onChange($event)">
      <option
        v-for="character in characters"
        :key="character.url"
          v-bind:value="character.url">
          {{ character[Object.keys(character)[0]] }}
        </option>
    </select>
    <ul>
      <li
        v-for="character in characters"
        :key="character.url"
        v-bind:id="character.url"
        class="li-character"
      >
        <ObjectDisplay v-bind:object="character" @clicked="onClickChild"/>
      </li>
    </ul>
  </div>
</template>

<script>
import {characters} from "../data/characters";
import ObjectDisplay from './ObjectDisplay.vue'

export default {
  name: 'AllCharacters',
  data() {
    return {
      characters: String
    };
  },
  components: {
    ObjectDisplay
  },
  created() {
    this.characters = characters;
  },
  methods: {
    onChange(event) {
      var divsToHide = document.getElementsByClassName("li-character"); //divsToHide is an array
      for(var i = 0; i < divsToHide.length; i++){
        divsToHide[i].style.display = "none"; // depending on what you're doing
      }
      document.getElementById(event.target.value).style.display = "block";
    },
    onClickChild(data) {
      characters.push(data) ;
      alert("The entry " + data[Object.keys(data)[0]] + " is added to the list.");
    }
  },
  mounted() {
    document.getElementById(characters[0].url).style.display = "block";
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#characters ul {
  list-style: none;
}

#characters ul li{
  display: none;
}

</style>
