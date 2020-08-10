<template lang="pug">
.todo__content
  todoInput(@addTodo="addTodo")
  todoList(
    v-if="todos.length > 0",
    :todos="filteredTodos",
    @removeTodo="removeTodo",
    @checkTodo="checkTodo",
    @filterTodos="filterTodos"
  )
</template>

<script>
import todoInput from "./todo-input";
import todoList from "./todo-list";
export default {
  data() {
    return {
      todos: [],
      filter: "All",
    };
  },
  components: {
    todoInput,
    todoList,
  },
  computed: {
    filteredTodos() {
      switch (this.filter) {
        case "All":
          return this.todos;
        case "Active":
          return this.todos.filter((item) => item.checked == false);
        case "Completed":
          return this.todos.filter((item) => item.checked);
      }
    },
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todos"));
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo); //добавляем объект todo в массив todos
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    removeTodo(todoId) {
      this.todos = this.todos.filter((item) => item.id != todoId);
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    checkTodo(todo) {
      this.todos = this.todos.map((item) => (item.id == todo.id ? todo : item));
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    filterTodos(filter) {
      this.filter = filter;
    },
  },
};
</script>

<style lang="scss" scoped>
.todo__content {
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.4), 0 25px 50px 0 rgba(0, 0, 0, 0.3);
  border-radius: 4px;
  width: 95%;
  margin: 50px auto;
  padding: 3px;
  background: gray;
}
</style>