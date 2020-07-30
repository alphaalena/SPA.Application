<template>
  <div class="list">
    <h1>Список  обязательных товаров: </h1>
    <add-list-component @add-list="addList"/>
    <hr>
    <list-component
      v-bind:lists="lists"
      v-on:remove-list="removeList"
    />
    <router-link to="/home">Главная</router-link>
  </div>
</template>
<script>
import ListComponent from '../components/list-component'
import AddListComponent from '../components/add-list-component'

export default {
  components: { AddListComponent, ListComponent },
  data () {
    return {
      lists: [
        {
          id: 1,
          title: 'Купи хлеб',
          completed: false
        },
        {
          id: 2,
          title: 'Купи мясо',
          completed: false
        },
        {
          id: 3,
          title: 'Купи мороженое',
          completed: false
        },
        {
          id: 4,
          title: 'Купи яйца',
          completed: false
        }
      ]
    }
  },
  methods: {
    removeList (id) {
      this.lists = this.lists.filter(l => l.id !== id)
    },
    addList (list) {
      this.lists.push(list)
    }
  }
}
</script>
