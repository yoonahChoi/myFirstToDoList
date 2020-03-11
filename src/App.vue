<template>
  <div id="app">
    <header class="header"><h1>ToDoList</h1></header>
    <input-box v-bind:value="newItem" v-on:@addItem="addItem"></input-box>
    <todo-list v-bind:list="items" v-on:@remove="removeItem"></todo-list>
  </div>
</template>

<script>
import InputBox from './components/InputBox.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'app',
  data () {
    return {
      newItem: '',
      items: [],
    }
  },
  created() {
    this.fetchList()
  },
  components: {
    'InputBox' : InputBox,
    'TodoList' : TodoList,
  },
  methods: {
    addItem(item) {
      this.newItem = item
      if(this.newItem !=='') {
        let value = this.newItem && this.newItem.trim()
        localStorage.setItem(value, value)
        this.items.push(value)
      }
    },
    fetchList() {
      if(localStorage.length > 0) {
        Object.keys(localStorage).forEach((item, index) => {
          if(localStorage.key(index) === localStorage.getItem(item)) this.items.push(localStorage.key(index))
        })
        this.items.sort()
      }
    },
    removeItem(item, index) {
      localStorage.removeItem(item)
      this.items.splice(index, 1)
    }
  }
}
</script>

<style>
.header{
  text-align: center;
  margin: 2em 1em;
  color: white;
  font-size: 25px;
  text-shadow: 5px 5px 5px rgba(0, 0, 0, 0.3);
}
.header h1{
  margin: 0;
}
</style>
