<template>
  <div>
    <h1>{{ tiitle }}</h1>
    <a :href="link">{{ link }}</a>
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
  },
})
</script>
