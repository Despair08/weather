<template>
  <div class="details">
    <div class="details__temp temp">
      <p class="temp__current">{{ temp }}&deg;C</p>
      <p class="temp__like">Feels like:</p>
      <p class="temp__feels-like">{{ likeTemp }}&deg;C</p>
    </div>
    <div class="details__descr descr">
      <img class="descr__icon" :src="iconUrl" alt="weather icon">
      <p class="descr__text">{{ descr }}</p>
    </div>
    <div class="cards cards">
      <ul class="cards__list">
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/humidity--dark.svg" alt="humidity_icon">
          <p class="item__value">{{ humidity }} %</p>
          <p class="item__descr">Humidity</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/wind--dark.svg" alt="wind_icon">
          <p class="item__value">{{ wind }} m/s</p>
          <p class="item__descr">Wind</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/cloud--dark.svg" alt="clouds_icon">
          <p class="item__value">{{ clouds }} %</p>
          <p class="item__descr">Clouds</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/pressure--dark.svg" alt="pressure_icon">
          <p class="item__value">{{ pressure }} hPa</p>
          <p class="item__descr">Pressure</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app-details',
  props: {
    city: String
  },
  data() {
    return {
      cityName: this.city,
      temp: null,
      likeTemp: null,
      descr: null,
      iconUrl: null,
      humidity: null,
      wind: null,
      pressure: null,
      clouds: null,
    }
  },
  async created() {
    const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.cityName}&units=metric&appid=04a6a9f964044e9e9f0286af4bc57f8b`);
    const weatherData = response.data;
    this.temp = Math.round(weatherData.main.temp);
    this.likeTemp = Math.round(weatherData.main.feels_like);
    this.descr = weatherData.weather[0].description;
    this.humidity = weatherData.main.humidity;
    this.wind = weatherData.wind.speed;
    this.clouds = weatherData.clouds.all;
    this.pressure = weatherData.main.pressure;
    this.iconUrl = `https://api.openweathermap.org/img/w/${weatherData.weather[0].icon}.png`;
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/details';
</style>