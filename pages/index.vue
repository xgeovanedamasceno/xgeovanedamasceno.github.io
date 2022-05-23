<template>
  <div>
    <h1 class="text-7xl font-black text-center">New on the blog</h1>
    <ul class="grid grid-cols-3 gap-8 mt-8">
      <PostPreview v-for="post in posts" :key="post.slug" :post="post"></PostPreview>
    </ul>
  </div>
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

      return {
        posts,
      }
  },
})
</script>
