<script>
export default {
  data: () => ({
    count: 0,
    counterTitle: 'Counter Standard',
    incrementAmount: 8
  }),
  computed: {
    displayTitle() {
      return this.count > 20 ? 'Counter High' : 'Counter Standard'
    },
    optimizedIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount
    }
  },
  methods: {
    incrementCount(newAmount) {
      this.count += this.optimizedIncrementAmount
    }
  }
}
</script>

<template>
  <div>
    <h1>{{ displayTitle }}</h1>
    <p>Count: {{ count }}</p>
    <p>Increment Amount: {{ optimizedIncrementAmount }}</p>
    <button @click="incrementCount">Increment</button>
    <div>
      <label for="incrementAmount">Increment Amount:</label>
      <input type="text" v-model="incrementAmount" />
    </div>
  </div>
</template>
