<template>
  <main class="container mx-auto p-8">
    <SEO :title="project.title" />
    <h1 class="text-5xl text-center font-bold mb-8 mx-auto">
      {{ project.title }}
    </h1>
    <div class="bg-white border shadow-md rounded-3xl p-4">
      <ul class="mb-4">
        <li><span class="font-semibold">Day</span>: {{ project.day }}</li>
        <li>
          <span class="font-semibold">Link</span>:
          <a class="link" :href="project.link">{{ project.link }}</a>
        </li>
      </ul>
      <nuxt-content :document="project" />
      <nuxt-link class="link text-lg font-bold" to="/">Back</nuxt-link>
    </div>
  </main>
</template>

<script lang="ts">
import { IContentDocument } from '@nuxt/content/types/content'
import Vue from 'vue'
import SEO from '../../components/SEO.vue'
export default Vue.extend({
  components: {
    SEO,
  },
  async asyncData({ route, $content }) {
    const day = Number.parseInt(route.params.day)
    const project = ((await $content('/')
      .where({ day: { $eq: day } })
      .fetch()) as unknown) as IContentDocument[]
    return { project: project[0] }
  },
})
</script>
