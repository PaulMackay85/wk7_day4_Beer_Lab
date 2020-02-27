<template>
  <div id="app">
    <h1>Beer List</h1>
    <beer-list :beers='beers'></beer-list>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)
  },
  components: {
    "beer-list": BeerList
   }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
