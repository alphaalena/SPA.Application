<template>
  <form v-on:submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Добавить</button>
  </form>
</template>
<script>
export default {
  name: 'addListComponent',
  data () {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit () {
      if (this.title.trim()) {
        const newList = {
          id: Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-list', newList)
        this.title = ''
      }
    }
  }
}
</script>
<style scoped>
  form{
    display: flex;
    justify-content: center;
  }
  input {
    width: 50%;
    height: 30px;
    margin: 20px;
    padding: 10px 20px;
    border: 1px solid grey;
    background-color: #d6d6d6;
    font-size: 16px;
  }
  button{
    margin: 30px 20px 20px;
    width: 100px;
    height: 40px;
    font-family: inherit;
    font-size: 15px;
    color: #111;
    text-decoration: none;
    text-shadow: 0 0 2px rgba(255, 255, 255, 1);
    background-color: #ccc;
    background-clip: padding-box;
    border: 1px solid;
    border-color: #202020 #1a1a1a #111;
    border-radius: 2px;
    background-image: -webkit-linear-gradient(top, #efefef, #777);
    background-image: -moz-linear-gradient(top, #efefef, #777);
    background-image: -o-linear-gradient(top, #efefef, #777);
    background-image: linear-gradient(to bottom, #efefef, #777);
    -webkit-box-shadow: inset 0 1px rgba(255, 255, 255, 0.09), 0 1px 1px rgba(0, 0, 0, 0.3);
    box-shadow: inset 0 1px rgba(255, 255, 255, 0.09), 0px 1px 1px rgba(0, 0, 0, 0.2);
  }
  .button:hover {
    background-color: #aaaaaa;
    background-image: -webkit-linear-gradient(top, #ccc, #555);
    background-image: -moz-linear-gradient(top, #ccc, #555);
    background-image: -o-linear-gradient(top, #ccc, #555);
    background-image: linear-gradient(to bottom, #ccc, #555);
  }
  .button:active, .button.active {
    background-color: #b42f32;
    border-color: #1c1c1c #202020 #222;
    -webkit-box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.3), 0 1px rgba(255, 255, 255, 0.09);
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.3), 0 1px rgba(255, 255, 255, 0.09);
  }
</style>
