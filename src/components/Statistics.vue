<script lang="ts">
export default {
  props: {
    characters: {
      type: Array,
      required: true
    }
  },
  computed: {
    percentLightSide() {
      const lightSide = this.characters.filter((character) => !character.isDark).length
      return Math.round((lightSide / this.characters.length) * 100)
    }
  }
}
</script>

<template>
  <div>
    <h1>Statistics</h1>
    <p>Percent Light Side: {{ percentLightSide }}%</p>
  </div>
</template>

<style scoped></style>
