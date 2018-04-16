<template>
  <form>
    <button @click="addTodoEvent()">ADD TODO</button>
    <button @click="removeTodo()">DELETE FINISHED TODOS</button>
    <p>input: <input type="text" v-model="newTodo"></p>
    <p>todo: {{ newTodo }}</p>
  </form>
</template>

<script>
export default {
  name: 'TodoForm',
  data:  function() {
    return {
      newTodo: ""
    }
  },
  methods: {
    addTodoEvent: function() {
      this.$emit('add-todo', this.newTodo)
    },
    removeTodo: function () {
      this.$emit('remove-done-todo')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@mixin flex-vender() {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
}

.todo-list {
  @include flex-vender;
  flex-direction: column;
  align-items: center;
}
</style>
