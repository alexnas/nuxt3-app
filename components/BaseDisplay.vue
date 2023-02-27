<script setup>
const props = defineProps({
  title: {
    type: String,
    default: 'List of Data',
  },
  itemType: {
    type: String,
    required: true,
  },
  itemList: {
    type: Array,
    default: [],
  },
});

const emit = defineEmits(['update:itemList']);

function fetchData() {
  fetch(`https://jsonplaceholder.typicode.com/${props.itemType}/`)
    .then((response) => response.json())
    .then((json) => emit('update:itemList', json));
}
</script>

<template>
  <section>
    <h1 class="title" style="color: blue">{{ title }}</h1>
    <button type="button" @click="fetchData">Fetch Data</button>
    <slot name="metrics" />
    <hr />
    <!-- <pre>{{ itemList }}</pre> -->
    <ul class="list">
      <slot name="items" />
    </ul>
  </section>
</template>
