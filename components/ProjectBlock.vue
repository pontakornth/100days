<template>
  <div class="p-4 mb-6 bg-white border border-gray-100 shadow-xl rounded-3xl">
    <h2 class="font-bold text-4xl mb-4 underline">
      <nuxt-link exact class="hover:text-blue-600" :to="`/day/${day}`">{{
        title
      }}</nuxt-link>
    </h2>
    <ul class="mb-4">
      <li><span class="font-semibold">Day</span>: {{ day }}</li>
      <li>
        <span class="font-semibold">Date</span>:
        {{ createdAt }}
      </li>
      <li>
        <span class="font-semibold">Link</span>:
        <a class="link" :href="link">{{ link }}</a>
      </li>
    </ul>
    <p class="nuxt-content">
      {{ document.description }}
      <span class="text-gray-500 underline"
        ><nuxt-link :to="`/day/${day}`">...more</nuxt-link></span
      >
    </p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    title: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
    day: {
      type: Number,
      required: true,
    },
    document: {
      type: Object,
      required: true,
    },
  },
  computed: {
    createdAt() {
      const createdDate = new Date((this as any).document.createdAt)
      return createdDate.toDateString()
    },
  },
})
</script>

<style>
.link {
  @apply text-blue-500 underline;
}
.link:hover,
.link:active {
  @apply text-blue-300;
}
</style>
