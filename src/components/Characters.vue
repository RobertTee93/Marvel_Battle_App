<template lang="html">
  <div>
    <h1 v-if="!selectedCharacter">Click to View</h1>
    <h2 v-if="selectedCharacter">Scroll for more</h2>
    <character-info :character="selectedCharacter"></character-info>
  <div id="character-select-grid">
    <div v-for="character of characters" v-on:click="getCharacterInfo(character)" class="character-select-icon">
      <img :src="getIcon(character)" :alt="character.name">
    </div>
  </div>
  </div>
</template>

<script>
import CharacterInfo from "./CharacterInfo.vue"
export default {
  name: "characters",
  data(){
    return {
      characters: null,
      selectedCharacter: null
    }
  },
  mounted(){
    fetch("https://marvel-battle-api.herokuapp.com/characters")
    .then(res => res.json())
    .then(data => this.characters = data)

  },
  methods: {
    getIcon(character){
      return require("../assets/icons/" + character.icon)
    },
    getCharacterInfo(character){
      this.selectedCharacter = character
      window.scrollTo(0, 90)
    }
  },
  components: {
    CharacterInfo
  }
}
</script>

<style lang="css" scoped>

#character-select-grid {
  display: flex;
  justify-content: center;
  margin: 0 400px;
  flex-wrap: wrap;
  margin-top: 50px;
}

.character-select-icon {
  width: 80px;
  height: 80px;
  border: white 2px solid;
  background-color: #404040cc;
  -webkit-filter: drop-shadow(5px 5px 5px #222);
  filter: drop-shadow(20px 20px 30px #222);
}

.character-select-icon:hover {
  background: #f50404;
}

.character-select-icon img {
  width: 80px;
  height: 80px;
}

h1 {
  text-align: center;
}

h2 {
  text-align: center;
  margin-top: 0;
}

@media only screen
and (max-width : 700px){
  #character-select-grid {
    display: flex;
    justify-content: center;
    margin: 0 5px;
    flex-wrap: wrap;
    margin-top: 50px;
  }
}

</style>
