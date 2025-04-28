<template>
  <div id="app" style="text-align: center; margin-top: 50px">
    <h1>Contador Realtime</h1>
    <h2>{{ counter }}</h2>

    <div style="margin-top: 20px">
      <button @click="decrement">-</button>
      <button @click="increment">+</button>
    </div>
  </div>
</template>

<script>
import { database, ref, onValue, set } from './Firebase.js'

export default {
  data() {
    return {
      counter: 0,
      counterRef: ref(database, 'counter'),
    }
  },
  created() {
    // Escuta atualizações em tempo real
    onValue(this.counterRef, (snapshot) => {
      if (snapshot.exists()) {
        this.counter = snapshot.val()
      }
    })
  },
  methods: {
    increment() {
      set(this.counterRef, this.counter + 1)
    },
    decrement() {
      set(this.counterRef, this.counter - 1)
    },
  },
}
</script>

<style>
button {
  font-size: 2rem;
  margin: 0 10px;
  width: 60px;
  height: 60px;
}
</style>
