<script>
import { reactive } from 'vue'

export default {
  async setup() {
    const state = reactive({
      users: []
    })

    async function fetchUsers() {
      const response = await fetch('https://jsonplaceholder.typicode.com/users').then((res) =>
        res.json()
      )

      return response
    }

    state.users = await fetchUsers()

    return {
      state
    }
  }
}
</script>

<template>
  <div v-for="user in state.users" :key="user.id">
    <h2>{{ user.name }}</h2>
    <p>{{ user.email }}</p>
  </div>
</template>

<style></style>
