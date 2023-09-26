<script lang="ts">
import { defineComponent } from 'vue';
import AppHeader from '@/components/AppHeader.vue';
import AppFilters from '@/components/AppFilters.vue';
import AppTodoList from '@/components/AppTodoList.vue';
import AppAddTodo from '@/components/AppAddTodo.vue';
import AppFooter from '@/components/AppFooter.vue';
import { Item } from '@/types/Item';
import { Filter } from '@/types/Filter';

interface State {
  items: Item[];
  activeFilter: Filter;
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
      activeFilter: 'All',
    };
  },

  computed: {
    filteredItems(): Item[] {
      switch (this.activeFilter) {
        case 'Active':
          return this.items.filter((item) => !item.status);
        case 'Done':
          return this.items.filter((item) => item.status);
        default:
          return this.items;
      }
    },
  },

  methods: {
    addItem(item: Item): void {
      this.items.push(item);
    },

    toggleItem(id: number): void {
      const targetItem = this.items.find((item: Item) => item.id === id);

      if (targetItem) {
        targetItem.status = !targetItem.status;
      }
    },

    removeItem(id: number): void {
      this.items = this.items.filter((item: Item) => item.id !== id);
    },

    setFilter(filter: Filter): void {
      this.activeFilter = filter;
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

        <AppFilters :active-filter="activeFilter" @set-filter="setFilter" />

        <main class="app-main">
          <AppTodoList
            :items="filteredItems"
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
