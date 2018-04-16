<template>
  <div class="todo-list__item"
       v-bind:class="{ 'todo-list__item--checked': todo.done }">
    <input type="checkbox" v-model="todo.done">
    <input type="checkbox" v-model="todo.editing">
    <input v-if="todo.editing" v-model="todo.text" @keyup.enter="todo.editing = !todo.editing">
    <span v-else>{{ todo.text }}</span>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: {
      required: true,
      type: Object,
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.todo-list {
  &__item {
    width: 270px;
    text-align: left;
    $element: #{&};
    &--checked {
      @extend #{$element};
      color: #85a6c6;
    }
  }
}
</style>
