<template>
  <div id="app">
    <Header />
    <div class="container">
     <div class="card mb-3 ">
          <Addtodo v-on:add-todo="addTodo"/>
     </div>
     <br/>

     <div class="card mb-3 ">
          <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
     </div>
  </div>
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';
import Addtodo from './components/Addtodo';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    Addtodo,
  },

  data() {
    return{
      todos: [
        {
          id: 1,
          tittle: "Todo one",
          completed: false
        },
        {
          id: 2,
          tittle: "Todo two",
          completed: true
        },
        {
          id: 3,
          tittle: "Todo three",
          completed: false
        }
      ]
    }
  }, 
  methods: {
    deleteTodo(id){
        this.todos = this.todos.filter(todo => todo.id != id);
    },

    addTodo(newTodo){
      this.todos = [...this.todos, newTodo];
    },
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }

</style>
