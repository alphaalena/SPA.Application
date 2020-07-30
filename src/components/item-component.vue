<template>
  <li>
    <span v-bind:class="{done: list.completed}">
        <input type="checkbox" v-on:change = "clickCheckbox">
      <strong class="ml">{{index + 1}}</strong>
      {{list.title | uppercase}}
    </span>
      <button class="remove"
              v-on:click="$emit('remove-list', list.id)"
      >&times;</button>
    </li>
</template>
<script>
export default {
  name: 'itemComponent',
  props: {
    list: {
      type: Object,
      REQUIRED: true
    },
    index: Number
  },
  methods: {
    clickCheckbox () {
      this.list.completed = !this.list.completed
    }
  },
  filters: {
    uppercase (value) {
      return value.toUpperCase()
    }
  }
}
</script>
<style scoped>
  .ml {
    margin-left: 10px;
  }
  li {
    border: 1px solid #4885F4;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding: 20px 10px;
    margin-bottom: 10px;
    background-color: #7eace9;
    box-shadow: #262525;
    border-radius: 10px;
  }
  .remove {
    background-color: #cb3e3e;
    color: white;
    border-radius: 50%;
    border: 1px solid red;
    font-weight: bold;
  }
  .done {
    text-decoration: line-through;
  }
</style>
