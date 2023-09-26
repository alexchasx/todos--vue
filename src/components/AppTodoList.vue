<script lang="ts">
import { PropType, defineComponent } from 'vue';
import AppTodoItem from '@/components/AppTodoItem.vue';
import { Item } from '@/types/Item';

export default defineComponent({
  components: {
    AppTodoItem,
  },

  props: {
    items: {
      type: Array as PropType<Item[]>,
    },
  },

  methods: {
    toggleItem(id: number) {
      this.$emit('toggleItem', id);
    },

    removeItem(id: number) {
      this.$emit('removeItem', id);
    },
  },

  emits: {
    toggleItem: (id: number) => Number.isInteger(id),
    removeItem: (id: number) => Number.isInteger(id),
  },
});
</script>

<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="item in items"
      :key="item.id"
      :item="item"
      @toggle-item="toggleItem"
      @remove-item="removeItem"
    />
  </ul>
</template>
