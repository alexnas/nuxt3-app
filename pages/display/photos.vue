<script setup>
import { ref, computed } from 'vue';
const route = useRoute();

const props = defineProps({
  title: {
    type: String,
    default: 'Photo Gallery',
  },
});

const itemList = ref([]);

const totally = computed(() => {
  return itemList.value;
});
</script>

<template>
  <div class="section">
    <NuxtPage v-if="route.params.id" />
    <BaseDisplay v-else :title="title" v-model:itemList="itemList">
      <template v-slot:metrics>
        <p>Totally: {{ totally.length }}</p>
      </template>
      <template v-slot:items>
        <li v-for="item in itemList" :key="item.id">
          <NuxtLink :to="`/display/photos/${item.id}`">
            <img :src="item.thumbnailUrl" :alt="item.title" />
            {{ item.title.slice(1, 10) }}...
          </NuxtLink>
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>
