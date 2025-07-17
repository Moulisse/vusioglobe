<script setup lang="ts">
import { ref } from 'vue';

const l = ref([1, 2, 3])
</script>

<template>
  <button @click="l.push(Math.random())">
    Add a random number
  </button>
  <ul>
    <li v-for="item of l" :key="item" @click="l = l.filter(i => i !== item)">
      {{ item }}
    </li>
  </ul>
</template>