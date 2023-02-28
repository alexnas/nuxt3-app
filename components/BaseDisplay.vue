<script setup>
const props = defineProps({
  title: {
    type: String,
    default: 'List of Data',
  },
  itemList: {
    type: Array,
    default: [],
  },
});

const route = useRoute();
const itemType = route.path.split('/').pop();
const emit = defineEmits(['update:itemList']);

onMounted(() => {
  fetch(`https://jsonplaceholder.typicode.com/${itemType}?_start=0&_limit=10`)
    .then((response) => response.json())
    .then((json) => emit('update:itemList', json));
});
</script>

<template>
  <section>
    <h1 class="title" style="color: blue">{{ title }}</h1>
    <slot name="metrics" />
    <hr />
    <ul class="list">
      <slot name="items" />
    </ul>
  </section>
</template>
