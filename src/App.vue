<template lang="pug">
  .wrapper
    todo
</template>

<script>
import todo from './components/todo';

export default {
  name: 'app',

  components: {
    todo
  },

  data () {
    return {
     
    }
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }

  html {
    width: 100%;
    height: 100%;
  }

  body {
    font-family: "Helvetica Neue", Helvetica, sans-serif;
    font-size: 16px;
    width: 100%;
    height: 100%;
    line-height: 1,42;
    font-weight: 500;
  }

  ul {
    list-style: none;
  }

  .wrapper {
    width: 100%;
    height: 100%;
    background: #eee6e6;
    display: flex;
    justify-content: center;
    align-items: flex-start;
  }

</style>
