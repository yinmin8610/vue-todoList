<template>
  <div id="app">
    <div class="container">
      <div class="tilte d-flex justify-content-center">
        <h1 class="h3">{{ title }}</h1>
      </div>
      <AddTodo v-on:addTodo="addTodoBtnClick"></AddTodo>
      <Nav></Nav>
      <Todo :todos="todolist" v-on:deleteTodo="deleteTodoBtnClick"></Todo>
      <div class="footer d-flex justify-content-between">
        <p>{{ counter }} tasks</p>
        <a href="#" @click="deleteAll">Clear All</a>
      </div>
    </div>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo'
import Nav from './components/Nav'
import Todo from './components/Todo'

export default {
  name: 'App',
  components: {
    AddTodo,
    Nav,
    Todo
  },
  methods: {
    addTodoBtnClick: function (todo) {
      let newTodo = todo
      let newId = Math.floor(new Date())
      // console.log(newTodo, newId)
      this.todolist.push({
        id: newId,
        title: newTodo,
        isCompleted: false
      })
      // console.log(this.todolist)
    },
    deleteTodoBtnClick: function (key) {
      // console.log(key)
      this.todolist.splice(key, 1)
    },
    deleteAll: function () {
      this.todolist = []
    }
  },
  computed: {
    counter: function () {
      let countArr = []
      this.todolist.forEach(function (item) {
        if (item.isCompleted === false) {
          countArr.push(item)
        }
      })
      return countArr.length
    }
  },
  data: function () {
    return {
      title: 'todoList',
      count: 0,
      todolist: [{ id: 0, title: '你好', isCompleted: false }]
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
body {
  background: #f4f7ff;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
