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
    toggleItem() {
      this.$emit('toggleItem', this.item.id);
    },

    removeItem() {
      this.$emit('removeItem', this.item.id);
    },
  },

  emits: {
    toggleItem: (id: number) => Number.isInteger(id),
    removeItem: (id: number) => Number.isInteger(id),
  },
});
</script>

<template>
  <li
    class="todo-item"
    :class="{ 'todo-item--done': item.status }"
    @click="toggleItem"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>

    <span class="todo-item__text">{{ item.text }}</span>

    <button class="todo-item__remove-button" @click.stop="removeItem">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>
