<template>
  <div class="container mt-5">
    <h1>Comentários</h1>
    <hr />
      <FormTodo v-on:add-todo="addComment" />
    <hr />

    <h3 v-if="comments.length <= 0">Sem comentários...</h3>
    <div class="list-group">
      <div class="list-group-item mb-4" v-for="(comment, index) in allComments" :key="index">
        <span class="comment_author">
          <strong>Autor:</strong> {{ comment.name }}
        </span>
        <p>
          <strong>Comentário:</strong> {{ comment.message }}
        </p>
        <div>
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
    }
  }
</script>