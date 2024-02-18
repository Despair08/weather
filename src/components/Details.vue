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
.details {
  grid-area: 2 / 4 / 4 / 8;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 25px;
  color: #fff;
  background-color: #444444;
  border-radius: 30px;
  box-shadow: 10px 10px 4px 0px rgba(0, 0, 0, 0.50);

  .temp {
    &__current {
      padding: 0 0 30px 0;
      font-size: 80px;
      font-weight: 700;
    }

    &__like {
      font-size: 20px;
    }

    &__feels-like {
      font-size: 70px;
      font-weight: 700;
    }
  }

  .descr {
    display: flex;
    flex-direction: column;
    align-items: center;

    &__icon {
      width: 120px;
      height: 120px;

    }

    &__text {
      font-size: 32px;
      font-weight: 600;
      text-align: center;
    }
  }

  .cards {

    &__list {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: repeat(2, 1fr);
      gap: 30px;
    }

    &__item {
      display: flex;
      flex-direction: column;
      gap: 10px;
      align-items: center;
      justify-content: space-between;
    }
  }
}

.item {
  &__icon {
    width: 60px;
    height: 60px;
  }

  &__value {
    font-size: 20px;
    font-weight: 600;
  }

  &__descr {
    font-size: 16px;
    font-weight: 500;
  }
}

span {
  font-size: 20px;
}
</style>