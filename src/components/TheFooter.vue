<template>
  <footer class="app-footer">
    {{ todos?.length }} more to do, {{ todos?.filter((todo) => todo.completed).length }} done
  </footer>
</template>

<script lang="ts">
import type { Todo } from '@/types/Todo.ts'

import { defineComponent, type PropType } from 'vue'
export default defineComponent({
  name: 'TheFooter',
  props: {
    todos: {
      type: Array as PropType<Todo[]>
    }
  }
})
</script>

<style scoped></style>
