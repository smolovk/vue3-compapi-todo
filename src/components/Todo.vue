<script setup>
import { ref } from 'vue'

defineProps({
  text: String
})

const emit = defineEmits(['delete'])

const isCompleted = ref(false);

function completeTodo() {
  isCompleted.value = !isCompleted.value;
}

function deleteHandler() {
    emit('delete')
}
</script>

<template>
  <li>
      <span :class="{ strike: isCompleted }"><slot></slot></span>
      <button @click="completeTodo" >{{ isCompleted ? 'X' : '✓' }}</button>
      <button @click="deleteHandler">🗑</button>
  </li>
</template>

<style scoped>
button {
    margin: 0 5px;
}

.strike {
  text-decoration: line-through;
  color: grey;
}
</style>
