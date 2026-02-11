<script setup>
defineProps(['players'])
const emit = defineEmits(['start'])

const hats = [
  { name: 'None', img: '' },
  {
    name: 'Top Hat',
    img: 'https://png.pngtree.com/element_our/20190529/ourmid/pngtree-a-black-top-hat-illustration-image_1214580.jpg',
  },
  {
    name: 'Crown',
    img: 'https://clipart-library.com/clip-art/cartoon-crown-transparent-background-15.htm',
  },
]

const shirts = [
  { name: 'None', img: '' },
  { name: 'Red Shirt', img: 'https://i.imgur.com/0Z8YQ9r.png' },
  { name: 'Blue Shirt', img: 'https://i.imgur.com/Qp9kR9A.png' },
]
</script>

<template>
  <div class="customizer">
    <h2>Customize Your Ducks</h2>

    <div v-for="(player, index) in players" :key="index" class="customizer__player">
      <h3>{{ player.name }}</h3>

      <label>Hat:</label>
      <select v-model="player.hat">
        <option v-for="hat in hats" :value="hat.img">{{ hat.name }}</option>
      </select>

      <label>Shirt:</label>
      <select v-model="player.shirt">
        <option v-for="shirt in shirts" :value="shirt.img">{{ shirt.name }}</option>
      </select>
    </div>

    <button class="customizer__start-btn" @click="emit('start')">Start Race</button>
  </div>
</template>

<style>
.customizer__player {
  margin: 10px;
}

.customizer__start-btn {
  padding: 10px 20px;
  font-size: 18px;
}
</style>
