<script lang="ts">
import { PropType, defineComponent } from 'vue';

export default defineComponent({
  props: {
    item: {
      type: Object as PropType<{
        id: number;
        text: string;
        status: boolean;
      }>,
      required: true,
    },
  },
});
</script>

<template>
  <li class="todo-item" :class="{ 'todo-item--done': item.status }">
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>

    <span class="todo-item__text">{{ item.text }}</span>

    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>
