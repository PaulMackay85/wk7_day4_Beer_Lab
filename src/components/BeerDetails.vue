<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <button @click="addOnClick">Add Favourite</button>
    <button @click="removeOnClick">Remove Favourite</button>
    <p>{{beer.description}}</p>
    <img :src="beer.image_url" alt="beer_pic">
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: "beer-details",
  props: ['beer', 'favouriteBeers'],
  methods: {
    addOnClick(){
      eventBus.$emit('add-to-fav', this.beer);
  },
    removeOnClick(){
      eventBus.$emit('remove-beer', this.beer);
    }
  }
}
</script>

<style lang="css" scoped>
img {
  height: 200px;
  width: auto;
}
</style>
