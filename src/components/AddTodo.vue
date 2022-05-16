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
  <li>
      <input type="text" placeholder="todo text" v-model="todoText">
      <button @click="addHandler">Add</button>
  </li>
</template>

<style scoped>
button {
    margin: 0 5px;
}
</style>
