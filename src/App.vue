<script>
// https://pokeapi.co/api/v2/pokemon?limit=151

import UserPage from '@/components/UserPage.vue'

export default {
  components: { UserPage },
  data: () => ({
    pokedex: [1, 2, 3]
  }),
  methods: {
    async fetchPokemon() {
      this.pokedex = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151').then((res) =>
        res.json()
      )
    }
  },
  created() {
    this.fetchPokemon()
  }
}
</script>

<!-- use @click.prevent to prevent default event behavior -->
<template>
  <h1>New App</h1>

  <user-page></user-page>
</template>

<style></style>
