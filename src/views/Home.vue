<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import Header from '../components/layout/Header';
import AddTodo from '../components/AddTodo';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Todos,
    Header,
    AddTodo,
  },
  data() {
    return {
      todos: [
        // {
        //   id: 1,
        //   title: 'Todo 1',
        //   completed: false,
        // },
        // {
        //   id: 2,
        //   title: 'Todo two',
        //   completed: true,
        // },
        // {
        //   id: 3,
        //   title: 'Todo three',
        //   completed: false,
        // },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then((res) => {
          console.log('delete', res);
          this.todos = this.todos.filter((todo) => todo.id !== id);
        })
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed,
        })
        .then((res) => {
          console.log('res.data', res.data);
          this.todos = [...this.todos, res.data];
        })
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=8')
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
