<template>
  <div id="app">
    <InventoryTree />
  </div>
</template>

<script>
import InventoryTree from './components/InventoryTree.vue'

export default {
  name: 'App',
  components: {
    InventoryTree
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
