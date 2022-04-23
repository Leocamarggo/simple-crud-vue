<template>
  <div class="container mt-5">
    <h1>Comentários</h1>
    <hr />
      <FormTodo v-on:add-todo="addComment" />
    <hr />
    <div class="list-group">
      <div class="list-group-item mb-4" v-for="(comment, index) in allComments" :key="comment.id">
        <span class="comment_author">
          <strong>Autor:</strong> {{ comment.name }}
        </span>
        <p>
          <strong>Comentário:</strong> {{ comment.message }}
        </p>
        <div>
          <button class="btn btn-warning">Editar</button>
          <button v-on:click="removeComment(index)" class="btn btn-danger">Excluir</button>
        </div>
      </div>
    </div>  
  </div>
</template>

<script>
  import FormTodo from './FormTodo'
  export default {
    components:{
      FormTodo
    },
    data() {
      return {
        comments: [],
      }
    },
    methods: {
      addComment(comment){
        this.comments.push(comment)
      },
      removeComment(index) {
        this.comments.splice(index, 1);
      }
    },
    computed: {
      allComments(){
        return this.comments.map(comment => ({
          ...comment,
          name: comment.name.trim() === '' ? 'Anônimo' : comment.name
        }))
      }
    },
    watch: {
      comments(value) {
        console.log(value);
      }
    }
  }
</script>