<script setup lang="ts">
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'
import Todo from './components/Todo.vue'
import Counter from './components/Counter.vue'

const text = ref('')
const state = ref(true)
const message = ref('Hello world!')
const childTitle = ref('Child title')
const childMsg = ref('No child message yet')

function toggle() {
  state.value = !state.value
}
</script>

<template>
  <h1>{{ message }}</h1>
  <Counter />
  <input placeholder="Write your own text" v-model="text" />
  <p>{{ text }}</p>
  <button @click="toggle">toggle state</button>
  <p v-if="state">Default</p>
  <p v-else>Toggled</p>
  <Todo />
  <ChildComp @response="(msg) => childMsg = msg" :msg="childTitle">Slotted text</ChildComp>
  <p>{{ childMsg }}</p>
</template>

<style>
html {
  background-color: #222222;
  color: #ffffff;
}
.done {
  text-decoration: line-through;
}
</style>