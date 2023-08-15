<script setup lang="ts">
defineProps<{
  user: string
}>()
</script>

<template>
  <h2>Hello {{ user }}</h2>
</template>
