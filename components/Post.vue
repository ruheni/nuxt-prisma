<template>
  <div @click="this.$router.push(`/p/${post.id}`)">
    <h2>{{ post.title }}</h2>
    <small>By {{ authorName }}</small>
    <p v-html="post.content"></p>
  </div>
</template>
<script>
export default {
  name: 'Post',
  props: {
    post: {
      type: Object,
      default: [],
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
