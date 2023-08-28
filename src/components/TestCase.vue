<script setup lang="ts">
import { computed, ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div class="btn-wrapper">
    <button
      @click="
        () => {
          $emit('counterEvent', 10)
        }
      "
    >
      Do something cool
    </button>
  </div>

  <div>{{ count }}</div>
</template>
