<template>
  <div class="hours">
    <h3 class="hours__title">Hourly forecast:</h3>
    <ul class="hours__list">
      <li v-for="(step, index) in   forecast  " :key="index" class="hours__item item">
        <span class="item__time">{{ getHour(step.time) }}</span>
        <img class="item__icon" :src="step.iconUrl" alt="card ico">
        <span class="item__value">{{ step.temperature }}&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico"
          v-bind:style="{ transform: getRotate(step.direction) }">
        <span class="item__wind-value">{{ step.wind }} m/s</span>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import moment from 'moment';

export default {
  name: 'hour-forecast', props: {
    city: String
  },
  data() {
    return {
      forecast: [],
      loading: true,
      iconUrl: null,
    }
  },
  mounted() {
    this.fetchWeatherData();
  },
  methods: {
    async fetchWeatherData() {
      const API_KEY = `04a6a9f964044e9e9f0286af4bc57f8b`;
      const city = this.city;
      const API_URL = `https://api.openweathermap.org/data/2.5/forecast?q=${city}&units=metric&appid=${API_KEY}`;
      await axios.get(API_URL).then(Response => {
        const forecastData = Response.data.list;
        const filteredData = forecastData.map(data => {
          return {
            step: moment(data.dt_txt.split(' ')[1]),
            time: moment(data.dt_txt),
            temperature: Math.round(data.main.temp),
            iconUrl: `https://api.openweathermap.org/img/w/${data.weather[0].icon}.png`,
            wind: data.wind.speed,
            direction: data.wind.deg,
          }
        }).reduce((acc, data) => {
          if (!acc.some(hour => hour.step.isSame(data.date, 'day'))) {
            acc.push(data);
          }
          return acc;
        }, []).slice(1, 6);
        this.forecast = filteredData;
      }).catch(error => {
        console.error(`Eror fetching data: ${error}`);
      });
    },
    getHour(hour) {
      return hour.format(`HH:mm`);
    },
    getRotate(val) {
      return `Rotate(${val}deg)`;
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/hourForecast';
</style>