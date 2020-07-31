<template>
  <div>
  <ul>
    <item-component v-for="(list, id) in lists"
                    v-bind:index="id"
                    v-bind:list="list"
                    @remove-list="removeList"
    ></item-component>
  </ul>
</div>
</template>
<script>
import ItemComponent from './item-component'
export default {
  name: 'listComponent',
  components: { ItemComponent },
  props: ['lists'],
  methods: {
    removeList (id) {
      this.$emit('remove-list', id)
    }
  }
}
</script>
<style scoped>
  ul {
    list-style: none;
    margin:0;
    padding: 0;
  }
</style>
