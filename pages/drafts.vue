<template>
  <div class="page">
    <h1>Drafts</h1>
    <main>
      <p v-if="$fetchState.pending">
        <span class="loading"></span>
      </p>
      <p v-else-if="$fetchState.error">Error while fetching drafts 🤬</p>
      <ul v-else>
        <li v-for="post in drafts" :key="post.id">
          <NuxtLink :to="`/p/${post.id}`">
            {{ post.title }}
          </NuxtLink>
        </li>
      </ul>
    </main>
  </div>
</template>
<script>  
export default {
  components: {},
  data() {
    return {
      drafts: [],
    }
  },
  async fetch() {
    const drafts = await fetch(`http://localhost:3000/api/drafts`).then((res) =>
      res.json()
    )
    this.drafts = drafts
  },
}
</script>
<style scoped>
.post {
  background: white;
  transition: box-shadow 0.1s ease-in;
}

.post:hover {
  box-shadow: 1px 1px 3px #aaa;
}

.post + .post {
  margin-top: 2rem;
}
</style>
