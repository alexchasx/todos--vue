<script lang="ts">
import { defineComponent } from 'vue';
import { Item } from '@/types/Item';

interface State {
  isFormVisible: boolean;
  itemText: string;
}

export default defineComponent({
  data() {
    return {
      isFormVisible: false,
      itemText: '',
    };
  },

  methods: {
    showForm(): void {
      this.isFormVisible = true;
    },

    closeForm(): void {
      this.isFormVisible = false;
    },

    addItem() {
      this.$emit('addItem', {
        id: Date.now(),
        text: this.itemText,
        status: false,
      });

      this.itemText = '';
    },
  },

  emits: {
    addItem: (item: Item) => item,
  },
});
</script>

<template>
  <section class="add-todo">
    <form v-if="isFormVisible" class="add-todo__form" @submit.prevent="addItem">
      <button class="close-button" type="button" @click="closeForm">
        <i class="bi bi-x"></i>
      </button>
      <div class="text-input text-input--focus">
        <input v-model="itemText" class="input" />
      </div>
      <button class="button button--filled">Add task</button>
    </form>

    <button v-else class="add-todo__show-form-button" @click="showForm">
      <i class="bi bi-plus-lg"></i>
    </button>
  </section>
</template>
