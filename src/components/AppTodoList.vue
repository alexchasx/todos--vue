<script lang="ts">
import { defineComponent } from 'vue';
import AppTodoItem from '@/components/AppTodoItem.vue';

interface State {
  items: {
    id: number;
    text: string;
    status: boolean;
  }[];
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
});
</script>

<template>
  <ul class="todo-list">
    <AppTodoItem v-for="item in items" :key="item.id" :item="item" />
  </ul>
</template>
