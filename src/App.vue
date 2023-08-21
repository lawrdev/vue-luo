<script setup lang="ts">
import GreetUser from './components/GreetUser.vue'
import TestCase from './components/TestCase.vue'
const sayThis = {
  user: 'KaunaJoe'
}
function runCount(n: number) {
  window.alert(`Heyyyy we got ${n}`)
}
</script>

<template>
  <GreetUser v-bind="sayThis" />

  <TestCase @counter-event="runCount" />
</template>

<style scoped></style>
