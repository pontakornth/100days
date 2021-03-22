<template>
  <main class="container">
    <h1 class="text-5xl text-center font-bold mb-8">100 Days of Code</h1>
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
  asyncData: async ({ $content }) => {
    const projects = await $content('/').fetch()
    return { projects }
  },
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  @apply p-4;
}
</style>
