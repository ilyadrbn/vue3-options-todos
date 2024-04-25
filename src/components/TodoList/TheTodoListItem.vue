<template>
  <li
    class="todo-item"
    :class="{ 'todo-item--done': todo.completed }"
    @click="$emit('toggleTodoStatus', todo)"
  >
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">{{ todo.text }}</span>
    <!-- * @click.stop для избежание отработки toggleTodoStatus в родительском элементе -->
    <TodoDeleteBtn @click.stop="$emit('removeTodo', todo)" />
  </li>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'
import type { Todo } from '@/types/Todo.ts'
import TodoDeleteBtn from './TodoDeleteBtn.vue'

export default defineComponent({
  name: 'TheTodoListItem',
  components: {
    TodoDeleteBtn
  },
  props: {
    // proxy object
    todo: {
      type: Object as PropType<Todo>,
      required: true
    }
  },
  // валидация передаваемого значения в emit
  emits: {
    toggleTodoStatus: (todo: Todo) => typeof todo === 'object',
    removeTodo: (todo: Todo) => typeof todo === 'object'
  }
})
</script>

<style scoped></style>
