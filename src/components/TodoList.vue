<template>
  <div>
    <form>
      <button @click="addTodo()">ADD TODO</button>
      <button @click="removeTodo()">DELETE FINISHED TODOS</button>
      <p>input: <input type="text" v-model="newTodo"></p>
      <p>todo: {{ newTodo }}</p>
    </form>
    <div class="todo-list">
      <template v-for="todo in todos">
        <todo-item :todo="todo"></todo-item>
      </template>
    </div>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  components: {
    TodoItem,
  },

  name: 'TodoList',
  data:  function() {
    return {
      msg: 'Welcome to Your Vue.js App',
      todos : [
        {text : 'vue-router', done: false, editing: false},
        {text : 'vuex', done: false, editing: false},
        {text : 'vue-loader', done: false, editing: false},
        {text : 'awesome-vue', done: true, editing: false},
      ],
      newTodo: ""
    }
  },
  methods: {
    addTodo: function(event) {
      let text = this.newTodo && this.newTodo.trim()
      if (!text) {
        return
      }
      this.todos.push({
        text: text,
        done: false,
        editing: false
      })
      this.newTodo = ''
    },
    removeTodo: function (event) {
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done) this.todos.splice(i, 1)
      }
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
