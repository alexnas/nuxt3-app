<script setup>
import { ref, computed } from 'vue';
const route = useRoute();

const props = defineProps({
  title: {
    type: String,
    default: 'Todo List',
  },
});

const itemList = ref([]);

const totally = computed(() => {
  return itemList.value;
});

const completedItems = computed(() => {
  return itemList.value.filter((item) => item.completed);
});

const remainingItems = computed(() => {
  return itemList.value.filter((item) => !item.completed);
});
</script>

<template>
  <div class="section">
    <NuxtPage v-if="route.params.id" />

    <BaseDisplay v-else :title="title" v-model:itemList="itemList">
      <template v-slot:metrics>
        <p>{{ totally.length }} totally || {{ completedItems.length }} completed || {{ remainingItems.length }} remaining</p>
      </template>
      <template v-slot:items>
        <li v-for="item in itemList" :key="item.id">
          <input type="checkbox" :checked="item.completed" />
          <NuxtLink :to="`/display/todos/${item.id}`">{{ item.title }}</NuxtLink>
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>
