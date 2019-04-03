<template lang="html">
  
</template>

<script>
export default {
<<<<<<< HEAD:src/components/Characters.vue
  name: "characters",
  data(){
    return {
      characters: null,
      selectedCharacter: null
    }
  },
  mounted(){
    fetch("http://localhost:3000/characters/")
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
=======
>>>>>>> parent of ea75198... added character viewer:client/src/components/Characters.vue
}
</script>

<style lang="css" scoped>
</style>
