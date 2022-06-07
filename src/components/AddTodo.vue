<script setup>
import { ref } from 'vue'

const todoText = ref()

const emit = defineEmits(['add'])

function addHandler() {
    if (todoText.value) {
        emit('add', todoText.value)
    }
    todoText.value = ''
}
</script>

<template>
  <div class="add-todo">
      <input type="text" placeholder="todo text" v-model="todoText">
      <button @click="addHandler">Add</button>
  </div>
</template>

<style scoped>
button {
    padding: 3px;
    margin: 5px;
    background: #2ECC71;
    border: 0;
    transition: .5s;
    color: #ECF0F1;
}

button:hover {
    background: #27AE60;
}

input { 
    color: #ECF0F1;
    background: #3498DB;
    border: 0;
    padding: 5px;
}
</style>
