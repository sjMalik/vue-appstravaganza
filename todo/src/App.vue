<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo APP</h1>
    <form @submit.prevent="addTodo()">
      <div class="form-group">
        <label for="todo">New Todo</label>
        <input v-model="newTodo" type="text" class="form-control" id="todo" aria-describedby="emailHelp" placeholder="Enter Todo Item">
        <!-- <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small> -->
      </div>
      <button type="submit" class="btn btn-success mt-2">Submit</button>
    </form>
    <ul class="list-group mt-3">
      <li class="list-group-item" v-for="(todo, i) in todos">
        <button class="btn btn-dark btn-sm" @click="markDone(todo)">Done</button>
        <button class="btn btn-danger btn-sm" @click="removeTodo(i)">Remove</button>
        <span :class="{isDone: todo.done}">{{ todo.title }}</span>
      </li>
    </ul>
  </div>
</template>
todo
<script>
export default {
  name: 'app',
  watch: {
    todos: {
      handler() {
        localStorage.todos = JSON.stringify(this.todos);
      },
      deep: true
    }
  },
  data () {
    return {
      newTodo: '',
      todos: []
    }
  },
  mounted(){
    if(localStorage.todos){
      this.todos = JSON.parse(localStorage.todos);
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false
      });
      this.newTodo = "";
    },
    markDone(todo){
      todo.done = true;
    },
    removeTodo(index){
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style scoped>
  .isDone{
    text-decoration: line-through;
  }
</style>
