<template>
  <div id="app">
    <header>
      <h1>Scooters</h1>
    </header>
    <scooters-component />
  </div>
</template>

<script>
import scootersComponent from './scootersComponent.vue'

export default {
  name: 'App',
  components: {
    scootersComponent
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
