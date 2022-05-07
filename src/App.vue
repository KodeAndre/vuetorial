<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

const counter = reactive({
  count: 0
})

const text = ref('')
const state = ref(true)
const message = ref('Hello world!')

let id = 0

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: false },
  { id: id++, text: 'Learn JavaScript', done: false },
  { id: id++, text: 'Learn Vue', done: false }
])
const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter(t => !t.done) : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}
function removeTodo(todo: any) {
  todos.value = todos.value.filter((t) => t !== todo)
}
function toggle() {
  state.value = !state.value
}
function increment() {
  counter.count++
}
function decrement() {
  counter.count--
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <input placeholder="Write your own text" v-model="text" />
  <p>{{ text }}</p>
  <button @click="toggle">toggle state</button>
  <p v-if="state">Default</p>
  <p v-else>Toggled</p>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" />
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
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