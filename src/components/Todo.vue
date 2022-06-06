<script setup>
import { ref } from 'vue'

defineProps({
  text: String
})

const emit = defineEmits(['delete'])

const isCompleted = ref(false);
const isDeleted = ref(false);

function completeTodo() {
  isCompleted.value = !isCompleted.value;
}

function deleteHandler(ev) {
  ev.preventDefault();
  isDeleted.value = true;
  setTimeout(() => emit('delete'), 500)
}
</script>

<template>
  <li @contextmenu="deleteHandler" @click="completeTodo" :class="{ delete: isDeleted, done: isCompleted }">
      <span><slot></slot></span>
      <!-- <button @click="completeTodo" >{{ isCompleted ? 'X' : '✓' }}</button>
      <button @click="deleteHandler">🗑</button> -->
  </li>
</template>

<style scoped>
button {
    margin: 0 5px;
}

.done {
  text-decoration: line-through;
  background: #27AE60;
  color: #BDC3C7;
}

.done:before {
  text-decoration: line-through;
  background: #27AE60;
}

.delete {
  background: #C0392B;
  opacity: 0;
}

.delete:hover {
  background: #C0392B;
}

.delete:before {
  background: #C0392B;
}

.delete:hover::before {
  background: #C0392B;
}
</style>
