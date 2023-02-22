<script>
import { defineNuxtComponent } from '#app';
export default defineNuxtComponent({
  data: () => ({
    todoList: [],
    photoGallery: [],
  }),
  computed: {
    numberOfPhotos() {
      return this.photoGallery.length;
    },
  },
  methods: {
    fetchTodoList() {
      fetch('https://jsonplaceholder.typicode.com/todos/')
        .then((response) => response.json())
        .then((json) => {
          this.todoList = json;
        });
    },
    fetchPhotos() {
      fetch('https://jsonplaceholder.typicode.com/photos/')
        .then((response) => response.json())
        .then((json) => {
          this.photoGallery = json;
        });
    },
  },
});
</script>

<template>
  <div>
    <img src="/todo.jpg" alt="Todo photo by Glenn Carstens-Peters" />
    <h1>Hello Frontend on the Nuxt!</h1>
    <button type="button" @click.prevent="fetchPhotos">Fetch photosList</button>
    <span> Whole set: {{ numberOfPhotos }} photos</span>
    <ul>
      <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
        <img :src="`${photo.thumbnailUrl}`" :alt="photo.title" />
        {{ photo.title }}
      </li>
    </ul>
    <button @click="fetchTodoList">Fetch Todo List</button>
    <ul>
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
