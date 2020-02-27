<template lang="html">
  <li>{{beer.name}}</li>
</template>

<script>
export default {
  name: 'beer-item',
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
