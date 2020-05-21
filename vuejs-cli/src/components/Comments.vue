<template>
<div class="container">
        <h1>Comentários</h1>
        <hr/>
        <div class="form-todo form-group">
            <p><input type="text" placeholder="Nome" name="author" class="form-control" v-model="name"></p>
            <p><textarea name="message"  placeholder="Comentário" class="form-control" v-model="message"></textarea></p>
            <button type="submit" class="btn btn-primary" v-on:click="addComment ">Comentar</button>
            <hr/>
        </div>
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="comment.index">
                <span class="comment__author">Autor:<strong>{{comment.name}}</strong></span>
                <p>{{comment.message}}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>  
</template>

<script>
export default{
data() {
        return {
            comments:[],
            name: '',
            message: ''
            }
        },
    methods:{
        addComment(){
                if(this.message.trim() ===''){
                    this.name = '';
                    this.message = '';
                    return
                }

                this.comments.push({
                    name:this.name,
                    message:this.message
                })

                this.name = '';
                this.message = '';
                },
            removeComment(index){
                this.comments.splice(index, 1);
            }
        },

        computed:{
            allComments(){
                return this.comments.map(comment =>({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anônimo': comment.name
                }));
            }
        },

                watch:{
                    comments(val){
                        console.log('val',val);
                    }
                }
    }

    
</script>

