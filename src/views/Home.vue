<template>
  <div class="home">
    <h1>Главная страница</h1>
    <section style="padding-bottom: 100px">Здесь должен быть раздел для главной, но я еще не придумала, что в нём</section>
    <hr>
    <router-link to="/list">Каталог</router-link>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'Home',
  components: {
  }
}
</script>
