<template lang="html">
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <p>{{beer.description}}</p>
    <img :src="beer.image_url" alt="beer_pic">
  </div>
</template>

<script>
export default {
  name: "beer-details",
  props: ['beer']
}
</script>

<style lang="css" scoped>
img {
  height: 200px;
  width: auto;
}
</style>
