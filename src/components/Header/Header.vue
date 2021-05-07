<template>
    <div class="bg-container1">
        <h1 class="heading">TODOS</h1>
        <div class="input-container">
        <h1 class="task-heading"><span class="small-heading">Create</span> Task</h1>
        <input type="text" class="input-element" placeholder="Whats needs to be done?" v-model="title" name="title"/>
        <button v-on:click="addTodo" class="btn">Add</button>
        <h1 class="task-heading1"><span class="small-heading">MY</span> Tasks</h1>
        </div>
    </div>
</template>
<script>
export default {
    name:'Header',
    data(){
        return{
            title:''
        }
    },
    methods:{
        addTodo(){
            const newTodo={
                title:this.title,
                completed:false
            }
            this.$emit('add-todo',newTodo);
            this.title='';
        }
    }
}
</script>
<style scoped>
.bg-container1{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.heading{
    margin-top:0px;
    padding-top:20px;
    font-size: 50px;
    font-weight: bold;
    font-family:cursive;
    color:rgb(4, 1, 20);
}
.task-heading{
font-size: 30px;
color:dimgray;
font-family:cursive;
text-align: left;
}
.task-heading1{
margin-top:50px;
font-size: 30px;
color:dimgray;
font-family:cursive;
text-align: left;
}
.small-heading{
    font-size: 50px;
    color:dimgray;
    font-weight: bold;
}
.input-container{
    width:50%;
    text-align: left;
}
.input-element{
    width:100%;
    height:40px;
    border-radius:20px;
    border:2px solid rgb(116, 119, 119);
    background-color: #969696;
    outline: none;
    font-size: 20px;
    color:snow;
    padding-left: 20px;
}
.btn{
    margin-top: 10px;
    background-color: dimgray;
    width:80px;
    height:40px;
    border:2px solid rgb(116, 119, 119);
    border-radius: 10px;
    color:white;
    font-size: 15px;
    margin-left: 10px;
}
</style>