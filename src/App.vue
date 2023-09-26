<script lang="ts">
import { defineComponent } from 'vue';
import AppHeader from '@/components/AppHeader.vue';
import AppFilters from '@/components/AppFilters.vue';
import AppTodoList from '@/components/AppTodoList.vue';
import AppAddTodo from '@/components/AppAddTodo.vue';
import AppFooter from '@/components/AppFooter.vue';

export default defineComponent({
  components: {
    AppHeader,
    AppFilters,
    AppTodoList,
    AppAddTodo,
    AppFooter,
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
          <AppTodoList />

          <AppAddTodo />
        </main>

        <AppFooter />
      </div>
    </body>
  </html>
</template>
