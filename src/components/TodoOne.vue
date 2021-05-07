<template>
<div class="items-container1">
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input class="box-check" type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
  </div>
  </div>
</template>

<script>
export default {
  name: "TodoOne",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
.items-container1{
    display: flex;
    justify-content: center;
    align-items: center;
}
  .todo-item {
    width:50%;
    background: #98a0a0;
    padding: 10px;
    border-radius: 20px;
    margin-bottom: 10px;
    border-bottom: 1px #ccc dotted;
    color:rgb(2, 5, 34);
    font-size: 20px;
  }
  .box-check{
      width:20px;
      height:20px;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: hsl(249, 100%, 50%);
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 30%;
    cursor: pointer;
    float: right;
    margin-right:10px;
  }
</style>