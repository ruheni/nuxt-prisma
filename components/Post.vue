<template>
  <div>
    <NuxtLink :to="`/p/${post.id}`">
      <h2>{{ post.title }}</h2>
      <small>By {{ authorName }}</small>
      <p v-html="post.content"></p>
    </NuxtLink>
  </div>
</template>
<script>
export default {
  props: {
    post: {
      id: Number,
      title: String,
      author: {
        name: String,
      },
      content: String,
      published: Boolean,
    },
  },
  computed: {
    authorName: post.author ? post.author.name : 'Unknown author',
  },
  name: 'Post',
}
</script>
<style scoped>
div {
  color: inherit;
  padding: 2rem;
}
</style>
