<template lang="pug">
.todo
  h1.todo__title MyTodoList
  todoContent
</template>

<script>
import todoContent from "./todo-content";

export default {
  components: {
    todoContent,
  },
};
</script>

<style lang="scss">
.todo {
  max-width: 700px;
  width: 60%;
  margin-top: 100px;
  text-align: center;
  padding-bottom: 50px;
  border-radius: 4px;
}

.todo__title {
  margin-top: 50px;
  text-shadow: 4px 3px 2px rgba(0, 0, 0, 0.4);
}
</style>