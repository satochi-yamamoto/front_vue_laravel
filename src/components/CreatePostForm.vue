<template>
  <div>
    <h2>Criar Post</h2>
    <form @submit.prevent="createPost">
      <label for="title">Título:</label>
      <input
        type="text"
        id="title"
        v-model="title"
        required
      />

      <label for="content">Conteúdo:</label>
      <textarea
        id="content"
        rows="5"
        v-model="content"
        required
      ></textarea>

      <button type="submit">Salvar</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CreatePostForm',
  data() {
    return {
      title: '',
      content: ''
    }
  },
  methods: {
    async createPost() {
      try {
        const payload = {
          title: this.title,
          content: this.content
        }

        await axios.post('http://127.0.0.1:8000/api/posts', payload)
        alert('Post criado com sucesso!')
        
        // Limpar campos
        this.title = ''
        this.content = ''
        
        // Se desejar, você pode emitir um evento ou fazer algo adicional
        // para atualizar a lista de posts no componente pai.
      } catch (error) {
        console.error('Erro ao criar post:', error)
      }
    }
  }
}
</script>
