<script>
import { ref, computed, reactive } from 'vue'

export default {
  async setup() {
    const regionName = ref('kanto')
    // You can use computedProperties instead, but it's good to be explicit
    // const regionNameAllCaps = computed(() => regionName.value.toUpperCase())

    const state = reactive({
      elemntType: 'lightning'
    })

    const regionNameAllCaps = computed(() => state.elemntType.toUpperCase())

    const pokedex = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151').then((res) =>
      res.json()
    )

    return {
      pokedex,
      regionName,
      regionNameAllCaps
    }
  },
  methods: {
    changeRegionName() {
      this.regionName = 'johto'
    }
  }
}
</script>

<template>
  <h2>{{ regionNameAllCaps }}</h2>
  <h3>{{ regionName }}</h3>
  <button @click="changeRegionName">Change Region</button>
  <pre>{{ pokedex }}</pre>
</template>
