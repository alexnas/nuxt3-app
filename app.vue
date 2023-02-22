<script>
import { defineNuxtComponent } from '#app';
export default defineNuxtComponent({
  data: () => ({
    todoList: [],
  }),
  methods: {
    fetchTodoList() {
      fetch('https://jsonplaceholder.typicode.com/todos/')
        .then((response) => response.json())
        .then((json) => {
          this.todoList = json;
        });
    },
  },
});
</script>

<template>
  <div>
    <img src="/todo.jpg" alt="Todo photo by Glenn Carstens-Peters" />
    <h1>Hello Frontend on the Nuxt!</h1>
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
