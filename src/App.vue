<template>
  <div id="app">
    <div class="wrapper">
      <div class="header">
        <div class="header__checkbox"></div>
        <input class="header__search" type="text" placeholder="Search your city" v-model="city">
        <button class="header__submit" @click="searchCity"><img class="submit__icon" src="@/assets/location.svg">
          Search</button>
      </div>
      <Location v-if="showWeather" :city="city"></Location>
      <Details v-if="showWeather" :city="city"></Details>
      <DayForecast v-if="showWeather" :city="city"></DayForecast>
      <HourForecast v-if="showWeather" :city="city"></HourForecast>
    </div>
  </div>
</template>

<script>
import Location from './components/Location.vue';
import Details from './components/Details.vue';
import DayForecast from './components/DayForecast.vue';
import HourForecast from './components/HourForecast.vue';

export default {
  name: 'App',
  components: {
    Location,
    Details,
    DayForecast,
    HourForecast
  },
  data() {
    return {
      city: '',
      showWeather: false,
    }
  },
  methods: {
    async searchCity() {
      this.showWeather = false;
      await this.$nextTick();
      this.city === '' ? this.showWeather = false : this.showWeather = true;
    }
  }
}
</script>

<style lang="scss">
@import '@/styles/common/normalize';
@import '@/styles/app';
</style>