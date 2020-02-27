<template lang="html">
  <div class="favs-list">
    <h2>Fav Beers</h2>
    <ul>
      <list-component v-for="(beer, index) in favBeers" :beer="beer" :key="index"></list-component>
    </ul>
  </div>
</template>

<script>
import ListComponent from './ListComponent.vue'

export default {
  name: 'favs-list',
  props: ['favBeers'],
  components: {
    'list-component': ListComponent
  }
}
</script>

<style lang="css" scoped>

  ul {
    list-style: none;
  }

</style>
