<script setup>
import { ref } from 'vue'

const text = ref('Hello')
</script>

<template>
  <input v-model="text" placeholder="Type here">
  <p>{{ text }}</p>
</template>