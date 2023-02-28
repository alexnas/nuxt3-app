<script setup>
import { ref, computed } from 'vue';

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
  <BaseDisplay :title="title" v-model:itemList="itemList">
    <template v-slot:metrics>
      <p>Totally: {{ totally.length }}</p>
    </template>
    <template v-slot:items>
      <li v-for="item in itemList" :key="item.id">
        <img :src="item.thumbnailUrl" :alt="item.title" />
        {{ item.title.slice(1, 10) }}...
      </li>
    </template>
  </BaseDisplay>
</template>
