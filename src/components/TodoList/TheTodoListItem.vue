<template>
  <!-- todo-item--done is a class for completed todo -->
  <li
    class="todo-item"
    :class="{ 'todo-item--done': todo.completed }"
    @click="$emit('toggleTodo', todo)"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">{{ todo.text }}</span>
    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'
import type { Todo } from '@/types/Todo.ts'

export default defineComponent({
  name: 'TheTodoListItem',
  props: {
    // proxy object
    todo: {
      type: Object as PropType<Todo>,
      required: true
    }
  },
  emits: {
    toggleTodo: (todo: Todo) => typeof todo === 'object' // валидация передаваемого значения в emit
  }
})
</script>

<style scoped></style>
