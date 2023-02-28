<script setup>
import { ref, computed } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();

const props = defineProps({
  title: {
    type: String,
    default: 'Todo List',
  },
});

const itemType = route.path.split('/').pop();
const itemList = ref([]);

const totally = computed(() => {
  return itemList.value;
});

const completed = computed(() => {
  return itemList.value.filter((item) => item.completed);
});
</script>

<template>
  <BaseDisplay :title="title" :itemType="itemType" v-model:itemList="itemList">
    <template v-slot:metrics>
      <p>Totally: {{ totally.length }} || Completed: {{ completed.length }}</p>
    </template>
    <template v-slot:items>
      <li v-for="item in itemList" :key="item.id">
        <input type="checkbox" :checked="item.completed" />
        <span>{{ item.title }}</span>
      </li>
    </template>
  </BaseDisplay>
</template>
