<template>
  <div class="page">
    <h1>My Blog</h1>
    <main></main>
    <p v-if="$fetchState.pending">
      <span class="loading"></span>
    </p>
    <p v-else-if="$fetchState.error">Error while fetching feed 🤬</p>
    <ul v-else>
      <li v-for="post in feed" :key="post.id">
        <NuxtLink :to="{ name: 'feed-slug', params: { slug: post.slug } }">
          {{ post.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      feed: [],
    }
  },
  activated() {
    if (this.$fetchState.timestamp <= Date.now() - 30000) {
      this.$fetch()
    }
  },
  async fetch() {
    this.feed = await this.$http
      .$get('http://localhost:3000/api/feed')
      .then((res) => res.json())
  },
}
</script>

<style>
.post {
  background: white;
  transition: box-shadow 0.1s ease-in;
}

.post:hover {
  box-shadow: 1px 1px 3px #aaa;
}

.post,
.post {
  margin-top: 2rem;
}
</style>
