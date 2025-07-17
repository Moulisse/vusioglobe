<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p v-if="counter === 0">Count is zero</p>
  <p v-else-if="counter <= 1">Count is one</p>
  <p v-else>Count is too much</p>
  <button @click="counter++">+1</button>
</template>
