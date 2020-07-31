<template>
  <div class="list">
    <h1>Список  обязательных товаров: </h1>
    <router-link to="/home">Главная</router-link>
    <hr>
    <add-list-component @add-list="addList"/>
    <select class="filter" v-model="filter">
      <option value="all">Весь список</option>
      <option value="completed">Завершенные</option>
      <option value="not-completed">Не завершенные</option>
    </select>
    <loader-component v-if="loading"/>
    <list-component
      v-else-if="filterLists.length"
      :lists="filterLists"
      @remove-list="removeList"
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
      loading: true,
      filter: 'all'
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
  },
  computed: {
    filterLists () {
      if (this.filter === 'all') {
        return this.lists
      }
      if (this.filter === 'completed') {
        return this.lists.filter(l => l.completed)
      }
      if (this.filter === 'not-completed') {
        return this.lists.filter(l => !l.completed)
      }
    }
  }
}
</script>
<style scoped>
  .paragraph {
    font-size: 24px;
    color: #1c1c1c;
    text-decoration: ActiveBorder;
  }
  .filter{
    padding: 10px;
    margin: 20px;
    width: 400px;
    text-transform: uppercase;
    text-align: center;
    background-color: #aeaeae;
  }
</style>
