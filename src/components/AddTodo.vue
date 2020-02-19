<template>
  <div class="AddTodo">
      <form>
        <div class="form-row my-3">
          <div class="col-10">
            <input type="text" class="form-control form-control-lg" placeholder="Todo . . ." v-model="inputValue" @keyup.13="addTodo"/>
          </div>
          <div class="col-2">
            <button type="button" class="btn btn-primary btn-block btn-lg" @click="addTodo">ADD</button>
          </div>
        </div>
      </form>
    </div>
</template>

<script>
export default {
  name: 'AddTodo',
  data: function () {
    return {
      inputValue: ''
    }
  },
  methods: {
    addTodo: function () {
      this.$emit('addTodo', (this.inputValue))
    }
  }

}
</script>
