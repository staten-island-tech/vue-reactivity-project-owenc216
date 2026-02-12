<script setup>
import { ref } from 'vue'

const animals = [
  { name: 'Duck', emoji: '' },
  { name: 'Dog', emoji: '' },
  { name: 'Cat', emoji: '' },
  { name: 'Horse', emoji: '' },
]

const player1 = ref(animals[0])
const player2 = ref(animals[1])

const emit = defineEmits(['start'])

function startRace() {
  emit('start', [
    { ...player1.value, pos: 0 },
    { ...player2.value, pos: 0 },
  ])
}
</script>

<template>
  <div class="customizer">
    <h2>Pick Your Animal</h2>

    <div class="customizer__player">
      <h3>Player 1</h3>
      <select v-model="player1">
        <option v-for="a in animals" :key="a.name" :value="a">
          {{ a.name }}
        </option>
      </select>
    </div>

    <div class="customizer__player">
      <h3>Player 2</h3>
      <select v-model="player2">
        <option v-for="a in animals" :key="a.name" :value="a">
          {{ a.name }}
        </option>
      </select>
    </div>

    <button @click="startRace">Start Race</button>
  </div>
</template>

<style>
.customizer__player {
  margin: 10px;
}
</style>
