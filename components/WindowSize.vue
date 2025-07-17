<script setup lang="ts">
import { useMouse } from '@vueuse/core';

const { x, y } = useMouse()
</script>

<template>
  Pointer X : {{ x }}<br>
  Pointer Y : {{ y }}
</template>
