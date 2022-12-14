<template>
  <div id="app">
    <ProductsTable />
  </div>
</template>

<script>

import ProductsTable from './components/ProductsTable.vue'


export default {
  name: 'App',
  components: {
    ProductsTable,
  }
}
</script>

<style>
#app {
  color: #2c3e50;
  margin-top: 60px;
}
</style>
