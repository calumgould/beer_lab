<template lang="html">
  <li>{{beer.name}}</li>
</template>

<script>
export default {
  name: 'list-component',
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
