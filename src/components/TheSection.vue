<template>
  <aside class="app-filters">
    <section class="toggle-group">
      <button
        v-for="(section, index) in sections"
        :key="index"
        class="button"
        :class="{ 'button--primary': activeSection === section }"
        @click="$emit('toggleSection', section)"
      >
        {{ section }}
      </button>
    </section>
  </aside>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'

import type { Section } from '@/types/Section.ts'
import type { Todo } from '@/types/Todo.ts'

interface State {
  sections: Section[]
}

export default defineComponent({
  name: 'TheSection',
  data(): State {
    return {
      sections: ['All', 'Active', 'Done']
    }
  },
  props: {
    activeSection: {
      type: String as PropType<Section>,
      required: true
    }
  },
  emits: {
    toggleSection: (section: Section) => section
  }
})
</script>
<style scoped></style>
