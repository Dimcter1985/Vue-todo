<template lang="pug">
  .todo__filter
    button.todo__btn-filter(
      type="button"
      v-for="filter in filters"
      :class="{active: currentFilter == filter}"
      @click="filterTodos(filter)"
      ) {{filter}}
</template>

<script>
export default {
  data() {
    return {
      filters: ['All', 'Active', 'Completed'],
      currentFilter: 'All'
    }
  },
  methods: {
    filterTodos(filter) {
      this.currentFilter = filter;
      this.$emit('filterTodos', filter);
    }
  }
}
</script>

<style lang="scss" scoped>
  .todo__btn-filter {
  margin-right: 20px;
  border: none;
  background: transparent;
  font-weight: 300;
  color: inherit;
  cursor: pointer;
  border: 1px solid transparent;
  border-radius: 3px;
  outline: none;
  &.active {
    border-color: rgba(175, 47, 47, 0.2);
  }
  &:last-child {
    margin-right: 0;
  }
}
</style>