<script setup>
import { ref, computed } from 'vue';

defineProps({
  title: {
    type: String,
    default: 'Todo List',
  },
});

let todoList = ref([]);
const totallyItems = computed(() => {
  return todoList.value;
});

const completedItems = computed(() => {
  return todoList.value.filter((todo) => todo.completed);
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
  <div class="section">
    <slot name="hero" />
    <h1 class="title">{{ title }}</h1>
    <button @click="fetchTodoList">Fetch Todo List</button>
    <slot name="metrics" :completed="completedItems" :totally="totallyItems">
      <p>Totally: {{ totallyItems.length }} todos | Completed: {{ completedItems.length }} todos</p>
    </slot>
    <hr />
    <ul class="list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" />
        {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>
