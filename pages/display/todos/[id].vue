<script setup>
const route = useRoute();
</script>

<template>
  <h1 class="title">Task details</h1>
  <h2>This is task id {{ route.params.id }}</h2>
</template>
