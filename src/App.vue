<script>
import UserPage from '@/components/UserPage.vue'
import Pokedex from '@/components/Pokedex.vue'

export default {
  components: { UserPage, Pokedex }
}
</script>

<!-- use @click.prevent to prevent default event behavior -->
<template>
  <h1>New App</h1>

  <Suspense>
    <!--    <Pokedex />-->
    <UserPage />
    <!--    #fallback or v-slot:fallback -->
    <template #fallback>
      <p>Loading...</p>
    </template>
  </Suspense>

  <!--  <user-page></user-page>-->
</template>

<style></style>
