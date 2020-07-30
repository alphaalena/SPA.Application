<template>
  <div class="list">
    <h1>Список  обязательных товаров: </h1>
    <router-link to="/home">Главная</router-link>
    <hr>
    <add-list-component @add-list="addList"/>
    <loader-component v-if="loading"/>
    <list-component
      v-else-if="lists.length"
      v-bind:lists="lists"
      v-on:remove-list="removeList"
    />
    <p class="paragraph" v-else>Список пуст</p>
  </div>
</template>
<script>
import ListComponent from '../components/list-component'
import AddListComponent from '../components/add-list-component'
import LoaderComponent from '../components/loader-component'

export default {
  components: { LoaderComponent, AddListComponent, ListComponent },
  data () {
    return {
      lists: [],
      loading:true
    }
  },
  methods: {
    removeList (id) {
      this.lists = this.lists.filter(l => l.id !== id)
    },
    addList (list) {
      this.lists.push(list)
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=8')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.lists = json
          this.loading = false
        }, 500)
      })
  }
}
</script>
<style scoped>
  .paragraph {
    font-size: 24px;
    color: #1c1c1c;
    text-decoration: ActiveBorder;
  }
</style>
