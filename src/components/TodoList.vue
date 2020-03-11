<template>
  <div class="container center">
    <ul>
      <li class="shadow" v-for="(item, index) in items" :key="item">
        <span class="list-text" v-on:click="checkItem(index)">{{ item }}</span>
        <span class="btn-remove" type="button" v-on:click="removeItem(item, index)">X</span>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['list'],
  data() {
    return {
      items: this.list
    }
  },
  methods: {
    removeItem(item, index) {
      this.$emit('@remove', item, index)
    },
    checkItem(index) {
      document.getElementsByClassName('list-text')[index].classList.toggle('checked')
    }
  }

}
</script>

<style>
  .container {
    padding: 2em 0;
  }
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  li {
    position: relative;
    padding: 0 1em;
    height: 40px;
    line-height: 40px;
    background-color: #eee;
    margin: 0.7rem 0;
    border-radius: 5px;
  }
  li span {
    font-size: 13px;
  }
  .list-text {
    font-size: 16px;
  }
  .checked {
    color: gray;
    text-decoration: line-through;
  }
</style>
