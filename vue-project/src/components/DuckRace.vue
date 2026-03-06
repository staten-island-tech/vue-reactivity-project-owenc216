<script setup>
import { onMounted, ref } from 'vue'

const props = defineProps({
  players: Array,
})

const finishLine = 1700
const winner = ref(null)
function movePlayer(index) {
  if (!winner.value) {
    props.players[index].pos += 15

    if (props.players[index].pos >= finishLine) {
      winner.value = props.players[index].name
    }
  }
}
onMounted(() => {
  window.addEventListener('keydown', (e) => {
    if (e.key === 'w') movePlayer(0)
    if (e.key === 'ArrowUp') movePlayer(1)
  })
})
</script>

<template>
  <div class="race">
    <h2>Player 1: W | Player 2: ↑</h2>

    <div class="race-track">
      <div v-for="p in players" :key="p.name" class="race-duck" :style="{ left: p.pos + 'px' }">
        <img :src="p.img" class="race-img" />
        <p>{{ p.name }}</p>
      </div>
    </div>

    <h1 v-if="winner">{{ winner }} Wins!</h1>
  </div>
</template>

<style>
.race-track {
  position: relative;
  width: 1800px;
  height: 200px;
  border: 3px solid black;
  margin: auto;
  overflow: hidden;
}

.race-duck {
  position: absolute;
  top: 50px;
}

.race-img {
  width: 80px;
}
</style>
