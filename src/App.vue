<script lang="ts">
import { defineComponent } from 'vue';
import AppHeader from '@/components/AppHeader.vue';
import AppFilters from '@/components/AppFilters.vue';
import AppTodoList from '@/components/AppTodoList.vue';
import AppAddTodo from '@/components/AppAddTodo.vue';
import AppFooter from '@/components/AppFooter.vue';
import { Item } from '@/types/Item';

interface State {
  items: Item[];
}

export default defineComponent({
  components: {
    AppHeader,
    AppFilters,
    AppTodoList,
    AppAddTodo,
    AppFooter,
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
    addItem(item: Item) {
      this.items.push(item);
    },

    toggleItem(id: number) {
      const targetItem = this.items.find((item: Item) => item.id === id);

      if (targetItem) {
        targetItem.status = !targetItem.status;
      }
    },

    removeItem(id: number) {
      this.items = this.items.filter((item: Item) => item.id !== id);
    },
  },
});
</script>

<template>
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Todos</title>
      <link rel="stylesheet" href="./style.css" />
    </head>
    <body>
      <div id="app">
        <AppHeader />

        <AppFilters />

        <main class="app-main">
          <AppTodoList
            :items="items"
            @toggle-item="toggleItem"
            @remove-item="removeItem"
          />

          <AppAddTodo @add-item="addItem" />
        </main>

        <AppFooter />
      </div>
    </body>
  </html>
</template>
