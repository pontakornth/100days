<template>
  <nuxt-link
    :to="to"
    exact
    class="p-4 rounded bg-white hover:bg-gray-200 font-bold shadow-md"
  >
    <slot></slot>
  </nuxt-link>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    to: {
      type: String,
      required: true,
    },
  },
})
</script>
