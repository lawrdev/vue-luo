<script setup lang="ts">
import { ref } from 'vue'

const { bg } = defineProps({
  bg: {
    type: String,
    default: '#00000040'
  }
})
</script>

<template>
  <div class="container" :style="{ backgroundColor: bg }">
    <div class="head">
      <slot name="header00" :message="'BOYYYY1!'">HEAD</slot>
    </div>

    <main>
      <slot>Content</slot>
    </main>

    <div class="foot">
      <slot name="footer00">FOOTER</slot>
    </div>
  </div>
</template>
