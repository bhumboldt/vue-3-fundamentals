<script lang="ts">
export default {
  props: {
    character: {
      type: Object,
      required: true
    }
  },
  emits: ['favorited']
}
</script>

<template>
  <div>
    <span>{{ character.name }}</span>
    <button @click="$emit('favorited', character.name)">Favorite</button>
  </div>
</template>

<style scoped></style>
