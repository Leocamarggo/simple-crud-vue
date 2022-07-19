<template>
  <div class="form-todo form-group">
    <input v-model="name" placeholder="Nome" type="text" name="author" class="form-control mb-3">
    <textarea v-model="message" placeholder="Comentário" name="message" class="form-control mb-3"></textarea>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>
</template>

<script>
   export default {
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
        if(this.message.trim() === ''){
          return;
        }

        this.$emit('add-todo',{
          name: this.name, 
          message: this.message
        })

        this.name = '';
        this.message = '';
      }
    },
   }
</script>