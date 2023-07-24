<template>
  <div>
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <button v-on:click="addTodo">add</button>
    <Modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">
        warning<i
          class="fa-solid fa-business-time"
          @click="showModal = false"
        ></i>
      </h3>
      <h3 slot="body">warning</h3>
      <h3 slot="footer">warning</h3>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal-1.vue';
export default {
  data: function () {
    return {
      newTodoItem: '',
      showModal: false,
    };
  },
  methods: {
    addTodo: function () {
      if (this.newTodoItem !== '') {
        this.$emit('addTodoItem', this.newTodoItem);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput: function () {
      this.newTodoItem = '';
    },
  },
  components: {
    Modal: Modal,
  },
};
</script>

<style scoped>
.closeModalBtn {
  color: #42b983;
}
</style>
