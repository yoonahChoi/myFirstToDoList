<template>
  <div>
    <form v-on:submit.prevent="addItem" class="input-box">
      <input class="shadow" type="text" v-model="inputValue" v-on:Keyup="onKeyup" autofocus>
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
    onKeyup() {
      if(!this.inputValue.length) this.onReset()
    }
  },
}
</script>

<style>
  .input-box {
    position: relative;
    margin: 0 auto;
    width: 80%;
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
  .btn-reset{
    position: absolute;
    border-radius: 50%;
    background-color: #d3cff8;
    color: white;
    border: none;
    padding: 2px 5px;
    top: 7px;
    right: 10px;
  }
  .btn-reset::before {
    content: 'X';
  }
</style>
