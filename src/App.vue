<template>
  <div id="app">
    <div class="wrapper">
      <FormInput></FormInput>
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
import FormInput from "@/components/formInput/FormInput.vue";

export default {

  name: 'App',
  components: {
    FormInput,
    Location,
    Details,
    DayForecast,
    HourForecast
  },
  data() {
    return {
      city: '',
      showWeather: true,
    }
  },
  methods: {
    // async searchCity() {
    //   this.showWeather = false;
    //   await this.$nextTick();
    //   this.city === '' ? this.showWeather = false : this.showWeather = true;
    // }
  }
}
</script>

<style lang="scss">
@import '@/styles/common/normalize';
@import '@/styles/app';
</style>