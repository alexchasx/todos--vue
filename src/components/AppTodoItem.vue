<script lang="ts">
import { Item } from '@/types/Item';
import { PropType, defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: {
      type: Object as PropType<Item>,
      required: true,
    },
  },

  methods: {
    toggleTodo() {
      this.$emit('toggleTodo', this.item.id);
    },
  },

  emits: {
    toggleTodo: (id: number) => Number.isInteger(id),
  },
});
</script>

<template>
  <li
    class="todo-item"
    :class="{ 'todo-item--done': item.status }"
    @click="toggleTodo"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>

    <span class="todo-item__text">{{ item.text }}</span>

    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>
