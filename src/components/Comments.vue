<template lang="">
    <div class="container">
        <h1>Comentarios</h1>
        <hr>
        <FormTodo  @add-todo="addComment" />
        <div class="list-group">
          <p v-if="comments.length <= 0">Sem comentarios</p>
          <div class="list-group-item" v-for="(comment, index) in allComments" :key="index">
            <span class="comment_author">Autor: <strong>{{ comment.name }}</strong></span>
            <p>{{ comment.message }}</p>
            <div class="">
              <a href="#" title="Excluir" @click.prevent="removeComment(index)">Excluir</a>
            </div>
          </div>
        </div>
        <hr>
      </div>
</template>
<script>
import FormTodo from './FormTodo.vue'

export default {
  name: 'comments',
  components: {
    FormTodo
  },
  data() {
    return {
      comments: []
    }
  },

  methods: {
      addComment(comment) {
        this.comments.push(comment)
      },

      removeComment(index) {
        this.comments.splice(index, 1)
      }
    },

    computed: {
      allComments() {
        return this.comments.map(comment => ({
          ...comment,
          name: comment.name.trim() === '' ? 'Anonimo' : comment.name
        }))
      }
    },

    watch: {
      comments(val) {
        console.log('val',val)
      }
    }

}
</script>
<style lang="">
  
</style>