<template lang="html">
  <div class="beer-detail" v-if="beer">
    <div class="detail-wrapper">
      <h2><b>{{beer.name}}</b></h2>
      <div class="flex-wrapper">
        <div class="left">
          <p class="top"><b>{{beer.tagline}}</b></p>
          <p>{{beer.description}}</p>
          <p>ABV: <b>{{beer.abv}}%</b></p>
          <button type="button" @click="handleFavAdd">Add to Favourites</button>
        </div>
        <div class="right">
          <img :src="beer.image_url" :alt="beer.name">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    handleFavAdd(){
      eventBus.$emit('fav-beer-selected', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>

.beer-detail {
  box-sizing: border-box;
  height: fit-content;
  width: 60%;
  background: #eee;
  color: #222;
  padding: 10px;
  border: 1px solid #ccc;
}

.detail-wrapper {
  box-sizing: border-box;
  background: #fff;
  padding: 2em;;
  height: fit-content;
  border-radius: 3px;
  overflow: hidden;
}

.flex-wrapper {
  display: flex;
  justify-content: space-between;
}

.right {
  width: 45%;
  height: fit-content;
}

.left {
  width: 50%;
  height: fit-content;
}

.right img {
  min-height: 300px;
  max-height: 500px;
  padding-right: 2em;
}

.left p:first-child {
  margin-top: 0;
}

.left p {
  padding: 0.5em;
  margin-left: 0.5em;
  text-align: left;
  width: 100%;
  height: fit-content;
}

p.top {
  padding-top: 2em;
}

button {
  padding: 1em 3em;
  margin: 2em 1em;
  font-size: 1em;
  border-radius: 4em;
  background-color: #01c1e6;
  cursor: pointer;
  color: white;
}

button:hover {
  opacity: 80%
}

</style>
