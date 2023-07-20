<template>
  <div>
    <!-- <button v-on:click="clearTodo">Clear</button> -->
    <span v-on:click="clearTodo">Clear ALL</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo: function () {
      localStorage.clear();
    },
  },
};
</script>

<style></style>
