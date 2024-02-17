<template>
  <div id="app">
    <div class="wrapper">
      <Header></Header>
      <location></location>
      <Details></Details>
      <DayForecast></DayForecast>
      <HourForecast></HourForecast>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Location from './components/Location.vue';
import Details from './components/Details.vue';
import DayForecast from './components/DayForecast.vue';
import HourForecast from './components/HourForecast.vue';

export default {
  name: 'App',
  components: {
    Header,
    Location,
    Details,
    DayForecast,
    HourForecast,
  },
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

img {
  display: block;
}

ul {
  list-style-type: none;
}

html,
body {
  min-height: 100%;
}

#app {
  min-height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-image: linear-gradient(0deg, rgba(255, 255, 255, 0) 0%, rgba(56, 56, 56, 1) 100%);
  background-color: #1E1E1E;
}

.wrapper {
  display: grid;
  grid-template-columns: repeat(7);
  grid-template-rows: repeat(5);
  grid-column-gap: 45px;
  grid-row-gap: 45px;
  max-width: 1390px;
  margin: 0 auto;
  padding: 0 15px;


}
</style>