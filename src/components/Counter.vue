<script setup lang="ts">
import { reactive, watch } from 'vue'
const counter = reactive({
  count: 0
})
function increment() {
  counter.count++
}
function decrement() {
  counter.count--
}
watch(counter, (value) => {
  console.log("counterValue" ,value.count)
})
</script>

<template>
  <p>Count is: {{ counter.count }}</p>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
</template>