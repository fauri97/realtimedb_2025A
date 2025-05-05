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

<script setup>
import { ref, onMounted } from 'vue'
import { database } from '@/firebase'
import { ref as dbRef, onValue, set } from 'firebase/database'

const counter = ref(0)

onMounted(() => {
  const counterRef = dbRef(database, 'counter')
  
  onValue(counterRef, (snapshot) => {
    const data = snapshot.val()
    if (data !== null) {
      counter.value = data
    }
  })
})

function increment() {
  const counterRef = dbRef(database, 'counter')
  set(counterRef, counter.value + 1)
}

function decrement() {
  const counterRef = dbRef(database, 'counter')
  set(counterRef, counter.value - 1)
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
