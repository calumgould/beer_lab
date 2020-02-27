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
  background: #2c3e50;
  font-size: 16px;
  margin: 10px 0;
  padding: 0.5em;
  cursor: pointer;
  color: white;
  transition: 0.1s all ease-in;
  border-radius: 4em;
  margin: 0.5em 2em;
 }

 li:hover {
   opacity: 80%;
 }

</style>
