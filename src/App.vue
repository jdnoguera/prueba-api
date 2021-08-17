<template>
  <div>
    <table class="table table-success table-striped">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Título</th>
          <th scope="col">Usuario ID</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todos" :key="todo.id">
          <td>{{ todo.id }}</td>
          <td>{{ todo.completed }}</td>
          <td>{{ todo.title }}</td>
          <td>{{ todo.userId }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return {
      todos: null
    }
  },
  mounted(){
    this.getTodos();
  },
  methods: {
    getTodos(){
      axios
        .get('https://jsonplaceholder.typicode.com/todos')
        .then(response => {
          console.log(response)
          this.todos = response.data
        })
        .catch( e=> console.log(e))
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
