<script setup lang="ts">
import { ref } from 'vue'

const username = ref<string>()
</script>

<template>
  <p>Tab C</p>
  <input type="text" @input="username = ($event.target as HTMLInputElement).value" />
</template>
