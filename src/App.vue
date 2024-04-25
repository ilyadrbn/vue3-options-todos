<template>
  <TheHeader />
  <TheSection />

  <main class="app-main">
    <TheTodoList />
    <TheTodoInput />
  </main>

  <TheFooter />
</template>
<script lang="ts">
import TheHeader from '@/components/TheHeader.vue'
import TheSection from '@/components/TheSection.vue'
import TheTodoList from '@/components/TodoList/TheTodoList.vue'
import TheTodoInput from '@/components/TheTodoInput.vue'
import TheFooter from '@/components/TheFooter.vue'

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',
  components: {
    TheHeader,
    TheSection,
    TheTodoList,
    TheTodoInput,
    TheFooter
  }
})
</script>

<style scoped></style>
