<template>
  <div id="app">
    <h1>Beer List</h1>
    <div class="main-container">
      <beer-list :beers='beers'></beer-list>
      <beer-details :beer='selectedBeer' :favouriteBeers='favouriteBeers'></beer-details>
      <favourite-beers :favourites='favouriteBeers'></favourite-beers>
    </div>

  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import BeerDetails from './components/BeerDetails.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';
import {eventBus} from './main.js';

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },
  components: {
    "beer-list": BeerList,
    "beer-details": BeerDetails,
    "favourite-beers": FavouriteBeers
   }
}
</script>

<style>
.main-container {

}
</style>
