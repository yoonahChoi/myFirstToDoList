<template>
  <div id="app">
    <header class="header"><h1>ToDoList</h1></header>
    <input-box v-bind:value="newItem" v-on:@addItem="addItem"></input-box>
  </div>
</template>

<script>
import InputBox from './components/InputBox.vue'

export default {
  name: 'app',
  data () {
    return {
      newItem: ''
    }
  },
  components: {
    'InputBox' : InputBox,
  },
  methods: {
    addItem(item) {
      this.newItem = item
      if(this.newItem !=='') {
        let value = this.newItem && this.newItem.trim()
        localStorage.setItem(value, value)
      }
    },
  }
}
</script>
<style>
.header{
  text-align: center;
  margin: 1em;
}
.header h1{
  margin: 0;
}
.header h1:hover{
  color: #7f78d2;
}
</style>
