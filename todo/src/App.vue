<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo APP</h1>
    <form>
      <div class="form-group">
        <label for="todo">New Tod</label>
        <input type="email" class="form-control" id="todo" aria-describedby="emailHelp" placeholder="Enter email">
        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>
todo
<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
</style>
