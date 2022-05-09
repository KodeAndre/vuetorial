<script setup lang="ts">

const props = defineProps({
  msg: String
})
const emit = defineEmits(['response'])

emit('response', 'hello from child')
</script>
<template>
  <h2>{{ msg || "No props yet" }}</h2>
  <slot>Fallback</slot>
</template>

<style scoped>

</style>