<template>
  <ul>
    <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item">
      {{ todoItem.item }}
      <button v-on:click="removeTodo(todoItem, index)">삭제</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['propsdata'],

  methods: {
    removeTodo: function (todoItem, index) {
      this.$emit('removeItem', todoItem, index);
    },
  },
};
</script>

<style></style>
