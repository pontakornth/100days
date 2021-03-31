<template>
  <span></span>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'SEO',
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  head() {
    return {
      title: this.title,
      meta: [
        {
          property: 'og:image',
          content: `https://res.cloudinary.com/pontakorn/image/upload/c_scale,l_text:montserrat_200_bold:${encodeURI(
            this.title
          )},w_2000,co_white/v1617203477/pexels-kevin-ku-577585_yp8571.jpg`,
        },
      ],
    }
  },
})
</script>
