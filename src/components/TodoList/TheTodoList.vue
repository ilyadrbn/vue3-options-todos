<template>
  <ul class="todo-list" v-if="todos?.length">
    <TheTodoListItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggleTodoStatus="$emit('toggleTodoStatus', todo)"
      @removeTodo="$emit('removeTodo', todo)"
    />
  </ul>
</template>

<script lang="ts">
import TheTodoListItem from './TheTodoListItem.vue'
import type { Todo } from '@/types/Todo.ts'

import { defineComponent, type PropType } from 'vue'

export default defineComponent({
  name: 'TheTodoList',
  components: {
    TheTodoListItem
  },
  props: {
    todos: {
      type: Array as PropType<Todo[]>
    }
  },
  emits: {
    toggleTodoStatus: (todo: Todo) => typeof todo === 'object',
    removeTodo: (todo: Todo) => typeof todo === 'object'
  }
})
</script>
<style scoped></style>
