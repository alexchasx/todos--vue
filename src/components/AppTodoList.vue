<script lang="ts">
import { defineComponent } from 'vue';
import AppTodoItem from '@/components/AppTodoItem.vue';
import { Item } from '@/types/Item';

interface State {
  items: Item[];
}

export default defineComponent({
  components: {
    AppTodoItem,
  },

  data(): State {
    return {
      items: [
        { id: 1, text: 'Learn the basics of Vue', status: true },
        { id: 2, text: 'Learn the basics of Typescript', status: false },
        { id: 3, text: 'Learn the basics of Nuxt', status: false },
      ],
    };
  },

  methods: {
    toggleTodo(id: number) {
      const targetItem = this.items.find((item: Item) => item.id === id);

      if (targetItem) {
        targetItem.status = !targetItem.status;
      }
    },
  },
});
</script>

<template>
  <ul class="todo-list">
    <AppTodoItem
      v-for="item in items"
      :key="item.id"
      :item="item"
      @toggle-todo="toggleTodo"
    />
  </ul>
</template>
