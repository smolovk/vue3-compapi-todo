<script setup>
import { ref } from 'vue'
import Todo from './Todo.vue'

const todos = ref();

todos.value = [
  { text: 'todo text' },
  { text: 'another' },
  { text: 'third' }
]

function deleteTodo(todo) {
  todos.value = todos.value.filter(t => t.text !== todo.text)
}

function addTodo(text) {
  todos.value.push({ text })
}

defineExpose({
  addTodo,
});
</script>

<template>
  <ul v-for="todo in todos" :key="todo.text">
    <Todo @delete="deleteTodo(todo)">{{todo.text}}</Todo>
  </ul>
</template>

<style scoped>

ul {
  list-style: none;
  position: relative;
  transform: skewY(-15deg);
}

li { 
  position: relative;
  width: 200px;
  background: #2980B9;
  padding: 10px;
  transition: .5s;
  color: #ECF0F1
}

li:before {
  content: '';
  text-align: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: -40px;
  width: 40px;
  height: 100%;
  background: #2980B9;
  transition: .5s;
  transform-origin: right;
  transform: skewY(45deg);
}

li:hover {
  background: #3498DB;
}

li:hover::before {
  background: #3498DB;
}

</style>
