<template>
  <ul class="todo-list" v-if="todos.length">
    <TheTodoListItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggleTodo="() => (todo.completed = !todo.completed)"
    />
  </ul>
</template>

<script lang="ts">
import TheTodoListItem from './TheTodoListItem.vue'
import type { Todo } from '@/types/Todo.ts'

import { defineComponent } from 'vue'

interface State {
  todos: Todo[]
}
export default defineComponent({
  name: 'TheTodoList',
  components: {
    TheTodoListItem
  },
  data(): State {
    return {
      todos: [
        {
          id: 0,
          text: 'Learn the basics of Vue',
          completed: true
        },
        {
          id: 1,
          text: 'Learn the basics of Typescript',
          completed: false
        },
        {
          id: 2,
          text: 'Learn the basics of JavaScript',
          completed: true
        }
      ]
    }
  },
  methods: {
    // toggleTodo(item: Todo) {
    //   item.completed = !item.completed
    // }
  }
})
</script>
<style scoped></style>
