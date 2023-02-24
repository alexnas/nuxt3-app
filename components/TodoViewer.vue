<script setup>
import { ref, computed } from 'vue';

let todoList = ref([]);
const numberOfTodos = computed(() => {
  return todoList.value.length;
});

const numberOfCompletedTodos = computed(() => {
  return todoList.value.filter((todo) => todo.completed).length;
});

function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
    .then((response) => response.json())
    .then((json) => {
      todoList.value = json;
    });
}
</script>

<template>
  <img src="/todo.jpg" alt="Todo photo by Glenn Carstens-Peters" />
  <h1 class="title">Todo List</h1>
  <button @click="fetchTodoList">Fetch Todo List</button>
  <p>Whole set: {{ numberOfTodos }} todos</p>
  <p>Completed: {{ numberOfCompletedTodos }} todos</p>
  <ul class="list">
    <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
      <input type="checkbox" :checked="todo.completed" />
      {{ todo.title }}
    </li>
  </ul>
</template>

<style lang="scss">
@import './assets/styles/main.scss';

:root {
  --text-color: #{$textColor};
}
.heading {
  color: var(--text-color);
}

.list {
  color: var(--text-color);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
