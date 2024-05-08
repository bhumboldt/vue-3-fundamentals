<script>
export default {
  data: () => ({
    users: []
  }),
  methods: {
    async fetchUsers() {
      this.users = await fetch('https://jsonplaceholder.typicode.com/users').then((res) =>
        res.json()
      )
    }
  },
  created() {
    this.fetchUsers()
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
