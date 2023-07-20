<template>
  <ul>
    <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem">
      {{ todoItem }}
      <button v-on:click="removeTodo(todoItem, index)">삭제</button>
    </li>
  </ul>
</template>

<script>
export default {
  data: function () {
    return {
      todoItems: [],
    };
  },
  methods: {
    removeTodo: function (todoItem, index) {
      // console.log(todoItem, index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
  },
  created: function () {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
  },
};
</script>

<style></style>
