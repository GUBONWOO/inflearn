<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodoItem="addOneItem"></TodoInput>
    <TodoList2
      v-bind:propsdata="todoItems"
      v-on:removeItem="removeOneItem"
    ></TodoList2>
    <TodoFooter v-on:clearAll="clearAllItems"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList2 from './components/TodoList2.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  data: function () {
    return {
      todoItems: [],
    };
  },
  methods: {
    addOneItem: function (todoItem) {
      var obj = { completed: false, item: todoItem };
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeOneItem: function (todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
    clearAllItems: function () {
      localStorage.clear();
      this.todoItems = [];
    },
  },
  created: function () {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(
            JSON.parse(localStorage.getItem(localStorage.key(i)))
          );
        }
      }
    }
  },
  components: {
    TodoFooter,
    TodoHeader,
    TodoList2,
    TodoInput,
  },
};
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
