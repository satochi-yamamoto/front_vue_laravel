<template>
  <div>
    <h2>Lista de Posts</h2>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <strong>{{ post.title }}</strong> - {{ post.content }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PostsList',
  data() {
    return {
      posts: []
    }
  },
  async created() {
    try {
      const response = await axios.get('http://127.0.0.1:8000/api/posts')
      this.posts = response.data.data
      // De acordo com o nosso Resource,
      // 'data' no response contem a coleção de posts.
    } catch (error) {
      console.error('Erro ao buscar posts:', error)
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
}
</style>
