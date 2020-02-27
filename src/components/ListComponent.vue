<template lang="html">
  <li @click="handleClick">{{beer.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'list-component',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>

 li {
  list-style: none;
  display: block;
  background: #fff;
  font-size: 16px;
  margin: 10px 0;
  padding: 10px;
  cursor: pointer;
  color: #555;
  transition: 0.1s all ease-in;
  border-radius: 3px;
 }
 
</style>
