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
  middleware({ redirect }): void {
    return redirect(301, '/page/1')
  },
  asyncData: async ({ $content }) => {
    const projects = await $content('/').sortBy('day', 'desc').fetch()
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
