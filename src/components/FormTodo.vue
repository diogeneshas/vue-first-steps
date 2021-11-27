<template lang="">
  <div class="form-todo form-group">
    <p>
      <input type="text" placeholder="nome" name="author" class="form-control" v-model="name">
    </p>
    <p>
      <textarea name="message" placeholder="Comentario" class="form-control" v-model="message"></textarea>
    </p>
    <button type="submit" class="btn btn-primary mb-3" @click="addComment">Comentar</button>
  </div>
</template>
<script>
export default {
  name: 'FormTodo',
  data() {
    return {
      name: '',
      message: ''
    }
  },

  methods: {
    addComment() {
      if (this.message.trim() === '') {
        return
      }

      this.$emit('add-todo', {
        name: this.name,
        message: this.message
      })

      this.name = ''
      this.message = ''
    }
  }
}
</script>
<style lang="">
  
</style>