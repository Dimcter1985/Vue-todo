<template lang="pug">
.todo__field
  input.todo__input(
    type="text",
    placeholder="Введи текст и нажми Enter",
    autofocus,
    v-model="todo.name",
    @keydown.enter="addTodo"
  )
    //-передаем значение из инпут в поле name объекта todo, по нажатию клавиши enter вызываем метод addTodo
</template>

<script>
let uniqId = 0;
export default {
  data() {
    return {
      todo: {
        id: 0,
        name: "",
        checked: false,
      },
    };
  },
  methods: {
    addTodo() {
      uniqId++; //увеличиваем id на еденицу
      this.todo.id = uniqId; //присваеваем uniqId полю id объекта todo
      this.$emit("addTodo", { ...this.todo }); //передаем родителю метод addTodo и объект todo при помощи оператора spread
      this.todo.name = ""; //очищаем поле name объекта todo
    },
  },
};
</script>


<style lang="scss" scoped>
.todo__input {
  font-size: 24px;
  padding: 16px 16px 16px 60px;
  border: none;
  box-shadow: inset 0px 0px 10px 2px rgba(0, 0, 0, 0.2);
  line-height: 1.4em;
  outline: none;
  color: inherit;
  width: 100%;
  background: #fff;
  border-radius: 4px;

  &::placeholder {
    color: #d8d3d8;
  }
}
</style>