<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from 'vue'

import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'

const todoList = ref();

function addHandler(text) {
  todoList.value.addTodo(text);
}
</script>

<template>
  <div class="hint">
    Right-click to delete, left-click to mark as done
    <AddTodo @add="addHandler"/>
  </div>
  <TodoList ref="todoList" />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@500&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Quicksand', sans-serif;
}

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #2C3E50;
}

#app {
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
  min-height: 100vh;
}

.hint {
  color: #ECF0F1;
  text-align: center;
  margin-bottom: 5%;
}

.add-todo {
  margin: 10px auto; 
}
</style>
