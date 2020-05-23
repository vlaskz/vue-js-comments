<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormToDo v-on:add-todo="addComment"></FormToDo>
    <p v-if="comments.length <= 0">Sem comentários! Seja o primeiro!<br/>Muito obrigado por sua atenção!<br/>por <a href="http://github.com/vlaskz">Isaias Velasquez</a></p>
    <div class="list-group">
      <div
        class="list-group-item"
        v-for="(comment, index) in allComments"
        v-bind:key="comment.index"
      >
        <span class="comment__author">
          Autor:
          <strong>{{comment.name}}</strong>
        </span>
        <p>{{comment.message}}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import  FormToDo from './FormToDo'
export default {
  components:{
    FormToDo
  },
  data() {
    return {
      comments: []
    };
  },
  methods: {
    addComment(comment){
      this.comments.push(comment);
    },
    
    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },

  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name
      }));
    }
  },

  watch: {
    comments(val) {
      console.log("val", val);
    }
  }
};
</script>

