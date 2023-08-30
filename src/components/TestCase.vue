<script setup lang="ts">
const { userModifiers, user } = defineProps({
  user: String,
  userModifiers: { default: () => ({}) }
})
const emit = defineEmits(['update:user'])

function emitVal(e: Event) {
  let val = (e.target as HTMLInputElement).value

  // @ts-ignore
  if (userModifiers.capitalize) {
    val = val.charAt(0).toUpperCase() + val.slice(1)
  }

  emit('update:user', val)
}
</script>

<template>
  <input type="text" :value="user" @input="emitVal" />

  <p style="padding-top: 30px">We have {{ user }}</p>
</template>
