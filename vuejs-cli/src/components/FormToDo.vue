<template>
  <div class="form-todo form-group">
      <p>
        <input type="text" placeholder="Nome" name="author" class="form-control" v-model="name" />
      </p>
      <p>
        <textarea name="message" placeholder="Comentário" class="form-control" v-model="message"></textarea>
      </p>
      <button type="submit" class="btn btn-primary" v-on:click="addComment ">Comentar</button>
      <hr />
    </div>
</template>

<script>

export default {
    data() {
        return{
            name:'',
            message:''
        }
    },
    methods:{
    addComment() {
      if (this.message.trim() === "") {
        this.name = ""
        this.message = ""
        return;
      }

      this.$emit('add-todo',{
          name:this.name,
          message:this.message
      });   

     

      this.name = "";
      this.message = "";
    }
}

}
</script>

<style>

</style>