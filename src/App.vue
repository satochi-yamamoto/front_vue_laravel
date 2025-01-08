<template>
  <div id="app">
    <h1>Exemplo CRUD com Vue e Laravel 11</h1>
    <create-post-form />
    <posts-list />
  </div>
</template>

<script>
import PostsList from './components/PostsList.vue'
import CreatePostForm from './components/CreatePostForm.vue'

export default {
  name: 'App',
  components: {
    PostsList,
    CreatePostForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 20px;
}
</style>
