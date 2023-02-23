<script setup>
import { ref, computed } from 'vue';

let photoGallery = ref([]);

const numberOfPhotos = computed(() => {
  return photoGallery.value.length;
});

function fetchPhotos() {
  console.log('fetch Photos');
  fetch('https://jsonplaceholder.typicode.com/photos/')
    .then((response) => response.json())
    .then((json) => {
      photoGallery.value = json;
    });
}

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
  <div>
    <img src="/todo.jpg" alt="Todo photo by Glenn Carstens-Peters" />
    <h1>Hello Frontend on the Nuxt!</h1>
    <button type="button" @click.prevent="fetchPhotos">Fetch photosList</button>
    <p>Whole set: {{ numberOfPhotos }} photos</p>
    <ul>
      <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
        <img :src="`${photo.thumbnailUrl}`" :alt="photo.title" />
        {{ photo.title }}
      </li>
    </ul>
    <hr />
    <button @click="fetchTodoList">Fetch Todo List</button>
    <p>Whole set: {{ numberOfTodos }} todos</p>
    <p>Completed: {{ numberOfCompletedTodos }} todos</p>
    <ul :class="$style.list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" />
        {{ todo.title }}
      </li>
    </ul>
    <pre>
      {{ todoList }}
    </pre>
  </div>
</template>

<style module>
.list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
