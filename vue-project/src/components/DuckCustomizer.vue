<script setup>
import { ref } from 'vue'

const animals = [
  {
    name: 'Dog',
    img: 'https://png.pngtree.com/png-vector/20211231/ourmid/pngtree-running-dog-png-image_4119736.png',
  },
  { name: 'Duck', img: 'https://toppng.com/uploads/preview/donald-duck-11530971314bhzhdbacdf.png' },
  { name: 'Cat', img: 'https://toppng.com/uploads/preview/cat-11521380842tgtbawala1.png' },
  {
    name: 'Horse',
    img: 'https://images.rawpixel.com/image_png_800/czNmcy1wcml2YXRlL3Jhd3BpeGVsX2ltYWdlcy93ZWJzaXRlX2NvbnRlbnQvZnJob3JzZV9nYWxsb3BfY2FudGVyX21hcmUtaW1hZ2Utcm01MDMtbDBqOXJmcmgucG5n.png',
  },
]

const player1 = ref(animals[0])
const player2 = ref(animals[1])

const emit = defineEmits(['start'])

function startRace() {
  emit('start', [
    { name: player1.value.name, img: player1.value.img, pos: 0 },
    { name: player2.value.name, img: player2.value.img, pos: 0 },
  ])
}
</script>

<template>
  <div class="customizer">
    <h2>Pick Your Racer</h2>

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
