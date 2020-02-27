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
    fetch('https://api.punkapi.com/v2/beers?page=1&per_page=80')
    .then(res => res.json())
    .then(data => this.beers = [...this.beers, ...data])

    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    .then(res => res.json())
    .then(data => this.beers = [...this.beers, ...data])

    fetch('https://api.punkapi.com/v2/beers?page=3&per_page=80')
    .then(res => res.json())
    .then(data => this.beers = [...this.beers, ...data])

    fetch('https://api.punkapi.com/v2/beers?page=4&per_page=80')
    .then(res => res.json())
    .then(data => this.beers = [...this.beers, ...data])

    fetch('https://api.punkapi.com/v2/beers?page=5&per_page=80')
    .then(res => res.json())
    .then(data => this.beers = [...this.beers, ...data])

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })

    eventBus.$on('add-to-fav', (beer) => {
      if (beer['isFav'] === undefined){
      beer['isFav'] = true;
      this.favouriteBeers.push(beer);
      this.selectedBeer = null;
    }
    })

    eventBus.$on('remove-beer', (beer) => {
      let index = this.favouriteBeers.indexOf(beer);
      beer['isFav'] = undefined;
      this.favouriteBeers.splice(index, 1);
      this.selectedBeer = null;
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
