<template>
  <div id="app" class="bg-container">
    <Header v-on:add-todo="addTodo"/>
    <TodoAll v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    
  </div>
</template>

<script>
import Header from './components/Header/Header.vue'
import TodoAll from './components/TodoAll.vue'

export default {
  name: 'App',
  components: {
    Header,
    TodoAll
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      let url="https://jsonplaceholder.typicode.com/todos/"+id;
                let options = {
            method: "DELETE",
            headers: {
              "Content-Type": "application/json",
              Accept: "application/json",
            }
          };

          fetch(url, options)
            .then(function(response) {
              return response.json();
            })
      this.todos = this.todos.filter(todo => todo.id !==id)
    },
    addTodo(newTodo){
      let data = {
              title:newTodo.title,
              completed:newTodo.completed
              };

      let options = {
                method: "POST",
                headers: {
                  "Content-Type": "application/json",
                  Accept: "application/json",
                },
                body: JSON.stringify(data)
              };

      fetch("https://jsonplaceholder.typicode.com/todos", options)
                .then(function(response) {
                  return response.json();
                })
                    this.todos = [...this.todos,newTodo];
                  }
                },
  created(){
    let options={
      methods:"GET",
    }
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=10",options)
    .then(response =>response.json())
    .then(jsondata =>this.todos=jsondata)
    .catch(err=>console.log(err));
  }
  
}
</script>

<style scoped>
  .bg-container{
    margin-top:0px;
    background-color: rgba(245, 241, 240, 0.486);
    min-height: 100vh;
}
*{
  box-sizing: border-box;
  margin:0px;
}
</style>
