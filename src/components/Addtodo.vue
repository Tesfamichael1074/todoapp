<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="tittle" name="tittle"  placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>


<script>
import uuid from 'uuid';


export default {
    name: "Addtodo",
    data(){
      return {
          tittle: ''
      }  
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                tittle: this.tittle,
                completed: false
            }

            // send the todo

            this.$emit('add-todo', newTodo);
        }
    }
}
</script>


<style  scoped>
form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>