<template>
  <div>
    <h2>{{ post.title }}</h2>
    <small>By {{ authorName }}</small>
    <p v-html="post.content"></p>
  </div>
</template>
<script>
export default {
  name: 'Post',
  data() {
    return { post: {} }
  },
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
}
</script>
<style scoped>
div {
  color: inherit;
  padding: 2rem;
}
</style>
