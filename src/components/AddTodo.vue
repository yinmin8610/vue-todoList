<template>
  <div class="AddTodo">
      <form>
        <div class="form-row my-3">
          <div class="col-md-10">
            <input type="text" class="form-control" placeholder="Todo . . ." v-model="inputValue" />
          </div>
          <div class="col-md-2">
            <button type="button" class="btn btn-primary" @click="addTodo">ADD</button>
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
  // props: ['inputValue'],
  methods: {
    addTodo: function () {
      this.$emit('addTodo', (this.inputValue))
    }
  }

}
</script>
