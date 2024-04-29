<script>
// Vue 3
import Counter from '@/components/Counter.vue'
import Statistics from '@/components/Statistics.vue'

export default {
  components: { Statistics, Counter },
  data: () => ({
    characterNames: [
      { name: 'Luke Skywalker', isDark: false },
      {
        name: 'Darth Vader',
        isDark: true
      },
      { name: 'Obi-Wan Kenobi', isDark: false },
      { name: 'Yoda', isDark: false }
    ],
    favorites: [],
    newCharacter: {
      name: ''
    }
  }),
  computed: {
    percentLightSide() {
      const lightSide = this.characterNames.filter((character) => !character.isDark).length
      return Math.round((lightSide / this.characterNames.length) * 100)
    }
  },
  methods: {
    favoriteCharacter(name, event) {
      this.favorites.push(name)
      event.target.disabled = true
    },
    addNewCharacter() {
      this.characterNames.push(this.newCharacter.name)
      this.newCharacter.name = ''
    }
  }
}
</script>

<template>
  <h2>Characters</h2>
  <div id="app">
    <Counter />
    <hr />
    <label for="newCharacterName">New Character Name:</label>
    <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />

    <Statistics :characters="characterNames" />

    <h1>Favorite Characters</h1>
    <ul>
      <li v-for="favorite in favorites">{{ favorite }}</li>
    </ul>

    <h1>Characters</h1>
    <ul>
      <li v-for="character in characterNames">
        <span>{{ character.name }}</span>
        <button @click="favoriteCharacter(character.name, $event)">Favorite</button>
      </li>
    </ul>
  </div>
</template>
