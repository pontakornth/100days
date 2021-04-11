<template>
  <page-template :projects="projects" :page="1" />
</template>

<script lang="ts">
import Vue from 'vue'
import PageTemplate from '~/components/PageTemplate.vue'

export default Vue.extend({
  components: {
    PageTemplate,
  },
  asyncData: async ({ $content }) => {
    const projects = await $content('/')
      .sortBy('day', 'desc')
      .skip(0)
      .limit(5)
      .fetch()
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
