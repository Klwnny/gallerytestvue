<script setup>
import axios from 'axios'
import { ref } from 'vue'

const todos = ref([])

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
const { data } = await axios.get('https://jsonplaceholder.typicode.com/todos/').catch((error) => {
  alert(error)
})
todos.value = data

const variableBool = ref(true)

function toggle() {
  variableBool.value = !variableBool.value
}
</script>
<template>
  <div>
    <h2>Todo</h2>
    <button @click="toggle" v-if="variableBool">Gridify!</button>
    <button @click="toggle" v-else>CHANGE IT BACK OH GOD</button>

    <div v-if="variableBool">
      <div v-for="todo in todos" :key="todo.id">
        {{ todo.userId }} {{ todo.title }} - Completed: {{ todo.completed }}
        <button @click="removeTodo(todo)" class="outline">X</button>
      </div>
    </div>

    <div v-else class="grid">
      <div v-for="todo in todos" :key="todo.id">
        {{ todo.userId }} {{ todo.title }} - Completed: {{ todo.completed }}
        <button @click="removeTodo(todo)" class="outline">X</button>
      </div>
    </div>
  </div>
</template>
