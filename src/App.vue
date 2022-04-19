<template>
  <div id="app">
    <index-map/>
  </div>
</template>

<script>
  import IndexMap from './components/IndexMap.vue'

  export default {
    name: 'App',
    components: {
      IndexMap
    }
  }
</script>

<style>
  html,
  body,
  #app {
    height: 100%;
    margin: 0;
    padding: 0;
    border: 0
  }
</style>