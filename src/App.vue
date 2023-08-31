<script setup lang="ts">
import { ref } from 'vue'
import TestCase from './components/TestCase.vue'
import BaseLayout from './components/layout/BaseLayout.vue'
import TabA from './components/TabA.vue'
import TabB from './components/TabB.vue'
import TabC from './components/TabC.vue'

const userName = ref('metroe')
const activeTab = ref<string>('tabA')
const tabs = {
  tabA: TabA,
  tabB: TabB,
  tabC: TabC
}
</script>

<template>
  <test-case v-model:user.capitalize="userName" />

  <div style="margin: 50px 140px">
    <BaseLayout>
      <template #footer00> NEW FOOTER </template>
      <p>Content 1</p>
      <template v-slot:header00="{ message }"> NEW HEADER {{ message }} </template>
      <p>Content 2</p>

      <p>Content 3</p>
    </BaseLayout>
  </div>

  <h3>TABS</h3>
  <component :is="tabs[activeTab as keyof typeof tabs]" />

  <div style="margin-top: 20px; display: flex; gap: 20px">
    <button @click="activeTab = 'tabA'">TabA</button>
    <button @click="activeTab = 'tabB'">TabB</button>
    <button @click="activeTab = 'tabC'">TabC</button>
  </div>
</template>

<style scoped></style>
