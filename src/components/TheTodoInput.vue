<template>
  <section class="add-todo">
    <button class="add-todo__show-form-button" v-if="!isFormVisible" @click="toggleForm">
      <i class="bi bi-plus-lg"></i>
    </button>
    <form class="add-todo__form" @submit.prevent v-else>
      <button class="close-button" type="button" @click="toggleForm(), (todoText = '')">
        <i class="bi bi-x"></i>
      </button>
      <div class="text-input text-input--focus">
        <input class="input" v-model="todoText" placeholder="What needs to be done?" />
      </div>
      <button
        class="button button--filled"
        @click="
          $emit('addTodo', {
            id: Date.now(),
            text: todoText,
            completed: false
          } as Todo),
            (todoText = '')
        "
      >
        Add task
      </button>
    </form>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import type { Todo } from '@/types/Todo.ts'

interface State {
  isFormVisible: boolean
  todoText: string
}

export default defineComponent({
  name: 'TheTodoInput',
  data(): State {
    return {
      isFormVisible: false,
      todoText: ''
    }
  },
  emits: {
    addTodo: (todo: Todo) => typeof todo === 'object'
  },
  methods: {
    toggleForm() {
      this.isFormVisible = !this.isFormVisible
    }
  }
})
</script>
<style scoped></style>
