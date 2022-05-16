<script setup>
import { ref } from 'vue'
import Todo from './Todo.vue'
import AddTodo from './AddTodo.vue'

const todos = ref();

todos.value = [
  { text: '1' },
  { text: '2' },
  { text: '3' }
]

function deleteTodo(todo) {
  todos.value = todos.value.filter(t => t.text !== todo.text)
}

function addTodo(text) {
  todos.value.push({ text })
}
</script>

<template>
  <ul v-for="todo in todos" :key="todo.text">
    <Todo @delete="deleteTodo(todo)">{{todo.text}}</Todo>
  </ul>
  <AddTodo @add="addTodo($event)"></AddTodo>
</template>

<style scoped>
ul {
  list-style: none;
}
</style>
