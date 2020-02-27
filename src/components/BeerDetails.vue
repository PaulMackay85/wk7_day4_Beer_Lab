<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <button @click="handleClick">Add Favourite</button>
    <p>{{beer.description}}</p>
    <img :src="beer.image_url" alt="beer_pic">
  </div>
</template>

<script>
export default {
  name: "beer-details",
  props: ['beer', 'favouriteBeers'],
  methods: {
    handleClick(){
      console.log(this.beer['isFav']);
      if (this.beer['isFav'] === undefined) {
      this.beer['isFav'] = true;
      this.favouriteBeers.push(this.beer)
    }
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
