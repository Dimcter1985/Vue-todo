<template lang="pug">
  .todo__item(:class="{checked: todo.checked}")
    label.todo__label
      .todo__block
        input.todo__checkbox(
          type="checkbox"
          @change="checkTodo"
          :checked="todo.checked"
          )
      .todo__name {{todo.name}}
    button.todo__btn.todo__btn--view(type="button") v
    button.todo__btn(
      type="button"
      @click="removeTodo"
      ) x
</template>

<script>
export default {
  props: {
    todo: Object
  },
  methods: {
    removeTodo() {
      this.$emit('removeTodo', this.todo.id);
    },

    checkTodo(e) {
      const todoItem = {
        ...this.todo,
        checked: e.target.checked
      }
      this.$emit('checkTodo', todoItem);
    }
  }
}
</script>

<style lang="scss" scoped>
  .todo__item {
    display: flex;
    align-items: center;
    flex: 1;
    padding: 15px;

    &:last-child {
      border-bottom: 0 none;
    }

    &:hover {
      .todo__btn {
        visibility: visible;
      }
    }
  }

  .todo__label {
    display: flex;
    flex: 1;
  }

  .todo__name {
    padding-left: 15px;
    display: block;
    line-height: 1.2;
  }

  .checked .todo__name {
    text-decoration: line-through;
    color: rgb(216, 211, 211);
  }

  .todo__btn {
    background: transparent;
    border: none;
    color: firebrick;
    cursor: pointer;
    font-size: 22px;
    font-weight: 600;
    visibility: hidden;

    &--view {
      color: rgb(75, 178, 34);
      margin-right: 10px;
    }
  }
</style>