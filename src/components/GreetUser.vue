<script setup lang="ts">
const { user } = withDefaults(
  defineProps<{
    user: string
    title?: string
  }>(),
  { title: 'Oboyyyyy!' }
)
</script>

<template>
  <h2>Hello {{ user }} with {{ title }}</h2>
</template>
