<script setup>
import { onMounted } from 'vue'

const props = defineProps(['players'])
const finishLine = 600

function moveDuck(player) {
  player.position += 10
  if (player.position >= finishLine) {
    alert(player.name + ' WINS!')
    window.location.reload()
  }
}

onMounted(() => {
  window.addEventListener('keydown', (e) => {
    if (e.key === 'w') moveDuck(props.players[0])
    if (e.key === 'ArrowUp') moveDuck(props.players[1])
  })
})
</script>

<template>
  <div class="race">
    <div class="race__track">
      <div
        v-for="(player, index) in players"
        :key="index"
        class="race__duck"
        :style="{ left: player.position + 'px', top: index * 120 + 'px' }"
      >
        <img src="/src/assets/duck.png" class="race__duck-base" />

        <img v-if="player.hat" :src="player.hat" class="race__duck-hat" />
        <img v-if="player.shirt" :src="player.shirt" class="race__duck-shirt" />
      </div>
    </div>

    <p>Player 1: Press W | Player 2: Press ↑</p>
  </div>
</template>

<style>
.race__track {
  position: relative;
  width: 700px;
  height: 300px;
  border: 3px solid black;
  margin: auto;
}

.race__duck {
  position: absolute;
}

.race__duck-base {
  width: 100px;
}

.race__duck-hat {
  position: absolute;
  top: -40px;
  left: 20px;
  width: 50px;
}

.race__duck-shirt {
  position: absolute;
  top: 40px;
  left: 20px;
  width: 60px;
}
</style>
