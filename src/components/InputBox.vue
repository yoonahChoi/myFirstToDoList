<template>
  <div>
    <form v-on:submit.prevent="addItem" class="input-box center">
      <input class="shadow" type="text" v-model="inputValue" autofocus>
      <button v-show="inputValue.length" v-on:click="onReset" type="reset" class="btn-reset"></button>
    </form>
  </div>
</template>

<script>
export default {
  props: ['value'],
  data() {
    return {
      inputValue: this.value
    }
  },
  methods:{
    addItem() {
      this.$emit('@addItem', this.inputValue)
      this.onReset()
    },
    onReset() {
      this.inputValue = ''
    },
  },
}
</script>

<style>
  .input-box {
    position: relative;
  }
  input {
    border-style: none;
    box-sizing: border-box;
    width: 100%;
    padding: 0.6em;
  }
  input:focus {
    outline: none;
  }
</style>
