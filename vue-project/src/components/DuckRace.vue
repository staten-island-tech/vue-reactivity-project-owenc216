<script setup>
import { onMounted, ref } from 'vue'

const props = defineProps({
  players: Array,
})

const finishLine = 500
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
    <h2>Player 1: W key | Player 2: ↑ key</h2>

    <div class="race__track">
      <div v-for="p in players" :key="p.name" class="race__duck" :style="{ left: p.pos + 'px' }">
        {{ p.emoji }} {{ p.name }}
      </div>

      <div class="race__finish">🏁</div>
    </div>

    <h1 v-if="winner">{{ winner }} Wins!</h1>
  </div>
</template>

<style>
.race__track {
  position: relative;
  width: 600px;
  height: 150px;
  border: 3px solid black;
  margin: auto;
}

.race__duck {
  position: absolute;
  font-size: 40px;
}

.race__finish {
  position: absolute;
  right: 0;
  font-size: 40px;
}
</style>
