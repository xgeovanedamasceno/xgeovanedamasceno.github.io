<template>
  <h1>Hello There!</h1>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  async asyncData( { $content } ): Promise<{ posts: any }> {
    const posts = await $content()
      .only(['title', 'image',  'tags', 'slug'])
      .sortBy('createdAt', 'desc')
      .fetch()

      console.log("posts", posts)

      return {
        posts,
      }
  },
})
</script>
