<script setup lang="ts">
import { ref } from 'vue'
import GreetUser from './components/GreetUser.vue'
import TestCase from './components/TestCase.vue'

const userName = ref('metroe')
</script>

<template>
  <TestCase v-model:user.capitalize="userName" />
</template>

<style scoped></style>
