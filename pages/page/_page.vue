<template>
  <page-template
    :projects="paginatedProjects"
    :page="currentPage"
    :last-page="lastPage"
  />
</template>

<script lang="ts">
import Vue from 'vue'
import PageTemplate from '~/components/PageTemplate.vue'
export default Vue.extend({
  components: { PageTemplate },
  asyncData: async ({ $content, route, error }) => {
    const currentPage = parseInt(route.params.page)
    const perPage = 5
    const allProjects = await $content('/').fetch()
    const totalProjects = allProjects.length

    const lastPage = Math.ceil(totalProjects / perPage)
    let lastPageCount = totalProjects % perPage
    lastPageCount = lastPageCount === 0 ? perPage : lastPageCount
    const skipProject = () => {
      switch (currentPage) {
        case 1:
          return 0
        case lastPage:
          return totalProjects - lastPageCount
        default:
          return (currentPage - 1) * perPage
      }
    }
    const paginatedProjects = await $content('/')
      .sortBy('day', 'desc')
      .skip(skipProject())
      .limit(perPage)
      .fetch()

    if (currentPage === 0 || !paginatedProjects.length) {
      return error({ statusCode: 404, message: 'No projects found!' })
    }

    return { paginatedProjects, currentPage, lastPage }
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
