<script setup>
import TodoViewer from './components/TodoViewer.vue';
import PhotoGallery from './components/PhotoGallery.vue';
</script>

<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <TodoViewer />
        </div>
        <div class="column">
          <PhotoGallery />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import './node_modules/bulma/css/bulma.min.css'; // @import './node_modules/bulma/bulma.sass';
</style>
