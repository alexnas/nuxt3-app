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
</script>

<template>
  <h1 class="title">Photo Galery</h1>
  <button type="button" @click.prevent="fetchPhotos">Fetch photosList</button>
  <p>Whole set: {{ numberOfPhotos }} photos</p>
  <ul class="photo-galery-list">
    <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
      <img :src="`${photo.thumbnailUrl}`" :alt="photo.title" />
      {{ `${photo.title.slice(0, 10)}...` }}
    </li>
  </ul>
</template>

<style lang="scss">
.photo-galery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
