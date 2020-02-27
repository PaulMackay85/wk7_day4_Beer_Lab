<template lang="html">
  <div>
    <h1>Favourites</h1>
    <ul>
      <beer-item v-for="(beer, index) in favourites" :beer="beer" :key="index"></beer-item>
    </ul>
  </div>
</template>

<script>
import BeerItem from './BeerItem.vue';

export default {
  name: 'favourite-beers',
  props: ['favourites'],
  components: {
    'beer-item': BeerItem
  }
}
</script>

<style lang="css" scoped>
</style>
