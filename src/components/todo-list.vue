<template lang="pug">
  .todo__list-wrap
    ul.todo__list
      li.todo__item-wrap(
        v-for="todo in todos"
      )
        todoItem(
          :todo="todo"
          @removeTodo="removeTodo"
          @checkTodo="checkTodo"
        )
    .todo__footer
      .todo__footer-content
        .todo__counter {{todos.length}} items left
        todoFilter(
          @filterTodos="filterTodos"
        )
</template>

<script>
import todoItem from './todo-item'
import todoFilter from './todo-filter'
export default {
  props: {
    todos: Array
  },
    
  components: {
    todoItem,
    todoFilter
  },

  methods: {
    removeTodo(todoId) {
      this.$emit('removeTodo', todoId);
    },

    checkTodo(todo) {
      this.$emit('checkTodo', todo);
    },

    filterTodos(filter) {
      this.$emit('filterTodos', filter);
    }
  }
}
</script>

<style lang="scss"scoped>
  .todo__list-wrap {
    margin-top: 2px;
    border-radius: 4px;
    box-shadow: inset 0px 0px 10px 2px rgba(0, 0, 0, 0.2);
    background: #fff;
  }

  .todo__list {
    font-size: 24px;
    border-bottom: 1px solid #ededed;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
  }

  .todo__item-wrap {
    width: 100%;
    border-bottom: 1px solid #ededed;

    &:last-child {
      border-bottom: none;
    }
  }

  .todo__footer {
    color: #777;
    padding:  10px 15px;
    text-align: center;
    position: relative;
    font-size: 14px;
    border-radius: 4px;
  }

  .todo__footer-content {
    display: flex;
    align-items: center;
    position: relative;
  }

  .todo__filter {
    flex: 1;
  }
</style>