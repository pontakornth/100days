<template>
  <main class="container">
    <h1 class="text-5xl text-center font-bold mb-4">100 Days of Code</h1>
    <span class="block text-center text-2xl text-gray-500 mb-8"
      >Pontakorn Paesaeng (<a
        href="https://github.com/pontakornth"
        target="__blank"
        class="underline text-gray-600"
        >@pontakornth</a
      >)</span
    >
    <project-block
      v-for="project in projects"
      :key="project.day"
      :link="project.link"
      :day="project.day"
      :document="project"
      :title="project.title"
    />
  </main>
</template>

<script lang="ts">
import Vue from 'vue'
import ProjectBlock from '../components/ProjectBlock.vue'

export default Vue.extend({
  components: {
    ProjectBlock,
  },
  props: {
    projects: {
      type: Array,
      required: true,
    },
  },
})
</script>
