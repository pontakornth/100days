<template>
  <div class="p-4 border border-gray-100 shadow-xl">
    <h2 class="font-bold text-4xl mb-4">{{ title }}</h2>
    <ul class="mb-4">
      <li><span class="font-semibold">Day</span>: 1</li>
      <li>
        <span class="font-semibold">Link</span>:
        <a class="link" :href="link">{{ link }}</a>
      </li>
    </ul>
    <nuxt-content :document="document"></nuxt-content>
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
p {
  @apply mb-4;
}
</style>
