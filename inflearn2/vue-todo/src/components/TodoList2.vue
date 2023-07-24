<template>
  <div>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item">
        {{ todoItem.item }}
        <button v-on:click="removeTodo(todoItem, index)">삭제</button>
      </li>
    </transition-group>
  </div>
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

<style>
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>
