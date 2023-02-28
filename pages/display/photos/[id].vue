<script setup>
const route = useRoute();
</script>

<template>
  <h1 class="title">Photo details</h1>
  <h2 class="subtitle">This is photo id {{ route.params.id }}</h2>
</template>
