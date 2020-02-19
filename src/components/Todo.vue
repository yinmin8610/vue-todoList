<template>
  <div class="Todo">
    <ul class="p-0">
      <li class="todoInput" v-for="(item, key) in todos" :key="key" @dblclick="editTodo(item)">
        <div class="d-flex justify-content-between"  v-if="item.id !== cacheTodo.id">
        <div class="form-check">
          <input type="checkbox" class="form-check-input" :id="item.id" v-model="item.isCompleted" />
          <label class="form-check-label" :for="item.id">{{ item.title }}</label>
        </div>
        <a href="#" role="button" :key="key" @click="deleteTodo(key)">
          <font-awesome-icon :icon="['fas', 'times']" />
        </a>
        </div>
         <input type="text" class="form-control" v-if="item.id === cacheTodo.id" v-model="cacheTitle" @keyup.enter="doneTodoEdit(item)" @keyup.esc="cancelTodoEdit">
      </li>
    </ul>
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faTimes } from '@fortawesome/free-solid-svg-icons'
library.add(faTimes)

export default {
  name: 'Todo',
  props: ['todos'],
  data: function () {
    return {
      cacheTodo: {},
      cacheTitle: ''
    }
  },
  methods: {
    deleteTodo: function (key) {
      this.$emit('deleteTodo', key)
    },
    editTodo: function (item) {
      this.cacheTodo = item
      this.cacheTitle = item.title
    },
    doneTodoEdit: function (item) {
      item.title = this.cacheTitle
      this.cacheTitle = ''
      this.cacheTodo = {}
    },
    cancelTodoEdit: function () {
      this.cacheTodo = {}
    }
  }
}
</script>

<style lang="scss">
.Todo {
  .todoInput {
    list-style: none;
    border-radius: 5px;
    box-shadow: 3px 3px 6px 0 rgba(0, 0, 0, 0.16);
    background-color: #ffffff;
    padding: 15px;
    margin-bottom: 15px;
  }
  .form-check-input:checked+label{
    text-decoration: line-through
  }
}
</style>
