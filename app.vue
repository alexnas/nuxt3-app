<script setup>
import TodoViewer from './components/TodoViewer.vue';
import PhotoGalery from './components/PhotoGalery.vue';
</script>

<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <TodoViewer title="Welcome Todos!">
            <template v-slot:hero>
              <h2>Whoa this works!</h2>
            </template>
          </TodoViewer>
        </div>
        <div class="column">
          <PhotoGalery />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
</style>
