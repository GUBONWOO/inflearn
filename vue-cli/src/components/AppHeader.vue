<template>
  <header>
    <h1>{{ prosdata }}</h1>
    <button v-on:click="sendEvent">send</button>
  </header>
</template>

<script>
export default {
  props: ['prosdata'],
  methods: {
    sendEvent: function () {
      this.$emit('renew');
    },
  },
};
</script>

<style></style>
