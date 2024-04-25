<script setup lang="ts">
import TheHeader from '@/components/TheHeader.vue'
import TheSection from '@/components/TheSection.vue'
import TheTodoList from '@/components/TheTodoList.vue'
import TheTodoInput from '@/components/TheTodoInput.vue'
</script>

<template>
  <TheHeader />
  <TheSection />

  <main class="app-main">
    <TheTodoList />
    <TheTodoInput />
  </main>

  <footer class="app-footer">2 more to do, 1 done</footer>
</template>

<style scoped></style>
