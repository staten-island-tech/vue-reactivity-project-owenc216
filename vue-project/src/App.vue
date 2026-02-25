<script setup>
import { ref } from 'vue'
import DuckCustomizer from '@/components/DuckCustomizer.vue'
import DuckRace from '@/components/DuckRace.vue'
const players = ref([])
const gameStarted = ref(false)

function startGame(selectedPlayers) {
  players.value = selectedPlayers
  gameStarted.value = true
}
</script>

<template>
  <h1 class="title">Race Sum Ducks And Sum Other Things</h1>
  <h2 class="subtitle">No Harm Or Insult Intended</h2>
  <h3 class="instructions">w and up arrow key to move</h3>
  <DuckCustomizer v-if="!gameStarted" @start="startGame" />
  <DuckRace v-if="gameStarted" :players="players" />
</template>

<style scoped>
.title {
  text-align: center;
  margin-bottom: 20px;
  color: darkblue;
}

.subtitle {
  text-align: center;
  margin-bottom: 40px;
  font-style: italic;
  color: blueviolet;
}
.instructions {
  text-align: center;
  margin-bottom: 40px;
  font-style: italic;
  color: blueviolet;
}
</style>
