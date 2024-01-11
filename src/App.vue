<script setup>
import { ref, watch } from 'vue';
import Sortable from 'sortablejs';

const items = ref([
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 1, name: 'John' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Joe' },
]);

const list = ref();

watch(list, (val) => {
  if (val) {
    Sortable.create(val, {
      animation: 100,
      onEnd: (evt) => {
        const itemEl = evt.item;
        console.log(
          itemEl.from,
          itemEl.to,
          itemEl.oldDraggableIndex,
          itemEl.newDraggableIndex,
        );
      },
    });
  }
});
</script>

<template>
  <div
    class="container"
    ref="list"
  >
    <div
      v-for="item in items"
      :key="item.id"
      class="item"
    >
      {{ item.name }}
    </div>
  </div>
</template>

<style scoped>
div {
  user-select: none;
  list-style: none;
  padding: 0;
  margin: 0;
  padding: 10px;
  margin-bottom: 10px;
  background: #f0f0f0;
  border: 1px solid black;
  color: black;
}

.container {
  display: flex;
  width: 100%;
  flex-flow: row wrap;
}

.item:nth-child(odd) {
  background: #e0e0e0;
}
</style>
