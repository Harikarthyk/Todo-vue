<template>
  <div>
    <AppHeader title="Your Todo list" />
    <AddButton  
      @on-add="addTodo"
    />
    <TodoList
      :todoList="todoList"
      @on-complete="completeTodo"
      @on-delete="deleteTodo"
      @on-update="updateTodo"
    />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AddButton from './components/AddButton.vue';
import TodoList from './components/TodoList.vue';
export default {
  name: 'App',
  components: {
    AddButton,
    AppHeader,
    TodoList
},
  data() { 
    return {
      todoList: [{
        todoString: 'Task 1',
        completed: false,
        id: 12
      }]
    }
  },
  methods: {
    addTodo(todo) {
      this.todoList.push({
        todoString: todo,
        completed: false,
        id: new Date().toString()
      })
    },
    completeTodo(todoId) {
      this.todoList = this.todoList.map(_ => {
        if(_.id === todoId){
          _.completed = !_.completed;
        }
        return _
      })
    },
    deleteTodo(todoId) {
      this.todoList = this.todoList.filter(_ => _.id !== todoId)
    },
    updateTodo(todoId, todoString) {
      this.todoList = this.todoList.map(_ => {
        if(_.id === todoId){
          _.todoString = todoString;
        }
        return _
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
