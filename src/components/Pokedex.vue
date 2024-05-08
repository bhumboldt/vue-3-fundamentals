<script>
export default {
  async setup() {
    const regionName = 'kanto'

    const pokedex = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151').then((res) =>
      res.json()
    )

    return {
      pokedex,
      regionName
    }
  }
}
</script>

<template>
  <pre>{{ pokedex }}</pre>
</template>
