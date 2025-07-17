<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p>Count is: {{ counter }}</p>
  <button @click="counter++">+1</button>
</template>
