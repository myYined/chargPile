<template>
  <div id="app">
    <chart-I></chart-I>
  </div>
</template>

<script>
import chart_I from "./components/chart_I"
export default {
  name: 'App',
  components: {
    "chart-I": chart_I,
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
