<script>
// Vue 3
import Counter from '@/components/Counter.vue'
import Statistics from '@/components/Statistics.vue'
import CharacterCard from '@/components/CharacterCard.vue'
import BaseLayout from '@/components/BaseLayout.vue'

export default {
  components: { BaseLayout, CharacterCard, Statistics, Counter },
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
    characters() {
      return this.characterNames.map((character) => ({
        ...character,
        isFavorite: this.favorites.includes(character.name)
      }))
    }
  },
  methods: {
    favoriteCharacter(name) {
      this.favorites.push(name)
    },
    addNewCharacter() {
      this.characterNames.push(this.newCharacter.name)
      this.newCharacter.name = ''
    }
  }
}
</script>

<template>
  <BaseLayout>
    <template v-slot:one>
      <label for="newCharacterName">New Character Name:</label>
      <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />
    </template>
    <template v-slot:two>
      <h2>Characters</h2>
      <div id="app">
        <Counter />
        <hr />

        <Statistics :characters="characters" />

        <h1>Favorite Characters</h1>
        <ul>
          <li v-for="favorite in favorites">{{ favorite }}</li>
        </ul>

        <h1>Characters</h1>
        <ul>
          <li v-for="character in characters">
            <CharacterCard :character="character" @favorited="favoriteCharacter($event)" />
          </li>
        </ul>
      </div>
    </template>
  </BaseLayout>
</template>
