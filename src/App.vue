<template>
  <TheHeader />
  <TheSection :active-section="activeSection" :todos="todos" @toggle-section="toggleSection" />

  <main class="app-main">
    <TheTodoList
      :todos="filteredTodos"
      @toggle-todo-status="toggleTodoStatus"
      @remove-todo="removeTodo"
    />
    <TheTodoInput @add-todo="addTodo" />
  </main>

  <TheFooter :todos="todos" />
</template>
<script lang="ts">
import TheHeader from '@/components/TheHeader.vue'
import TheSection from '@/components/TheSection.vue'
import TheTodoList from '@/components/TodoList/TheTodoList.vue'
import TheTodoInput from '@/components/TheTodoInput.vue'
import TheFooter from '@/components/TheFooter.vue'

import type { Todo } from '@/types/Todo.ts'
import type { Section } from '@/types/Section.ts'

import { defineComponent } from 'vue'

interface State {
  todos: Todo[]
  activeSection: Section
}

export default defineComponent({
  name: 'App',
  components: {
    TheHeader,
    TheSection,
    TheTodoList,
    TheTodoInput,
    TheFooter
  },
  data(): State {
    return {
      todos: Array<Todo>(),
      activeSection: 'All'
    }
  },
  computed: {
    filteredTodos(): Todo[] {
      switch (this.activeSection) {
        case 'Active':
          return this.todos.filter((todo) => !todo.completed)
        case 'Done':
          return this.todos.filter((todo) => todo.completed)
        case 'All':
        default:
          return this.todos
      }
    }
  },
  methods: {
    addTodo(todo: Todo) {
      this.todos.push(todo)
    },
    toggleTodoStatus(todo: Todo) {
      todo.completed = !todo.completed
    },
    removeTodo(todo: Todo) {
      this.todos = this.todos.filter((item) => item.id !== todo.id)
    },
    toggleSection(section: Section) {
      this.activeSection = section
    }
  }
})
</script>

<style scoped></style>
