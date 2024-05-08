<script>
export default {
  async setup() {
    const users = await fetch('https://jsonplaceholder.typicode.com/users').then((res) =>
      res.json()
    )

    return {
      users
    }
  }
}
</script>

<template>
  <div v-for="user in users" :key="user.id">
    <h2>{{ user.name }}</h2>
    <p>{{ user.email }}</p>
  </div>
</template>

<style></style>
