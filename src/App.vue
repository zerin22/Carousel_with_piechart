<template>
  <div id="app">
    <div class="row">
      <div class="col-md-12">
        <carousel />
      </div>
      <div class="col-md-12">
        <pieChart />
      </div>

    </div>

  </div>
</template>

<script>
import Carousel from './components/Carousel.vue'
import PieChart from './components/PieChart.vue'

export default {
  name: 'App',
  components: {
    Carousel,
    PieChart
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #656565;
  margin-top: 10px;
}
</style>