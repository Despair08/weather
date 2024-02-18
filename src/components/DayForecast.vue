<template>
  <div class="days">
    <h3 class="days__title">Days forecast:</h3>
    <ul class="days__list">
      <li v-for="(day, idx) in forecast" :key="idx" class="days__item item">
        <img :src="day.iconUrl" alt="day icon" class="item__icon">
        <span class="item__value">{{ day.temperature }}&deg;C</span>
        <span class="item__date">{{ getDay(day.date) }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import moment from 'moment';
export default {
  name: 'day-forecast',
  props: {
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
            date: moment(data.dt_txt.split(' ')[0]),
            temperature: Math.round(data.main.temp),
            iconUrl: `https://api.openweathermap.org/img/w/${data.weather[0].icon}.png`,
          }
        }).reduce((acc, data) => {
          if (!acc.some(day => day.date.isSame(data.date, 'day'))) {
            acc.push(data);
          }
          return acc;
        }, []).slice(1, 6);
        this.forecast = filteredData;
      }).catch(error => {
        console.error(`Eror fetching data: ${error}`);
      });
    },
    getDay(date) {
      return date.format(`ddd, D MMM`);
    }
  }
}
</script>

<style lang="scss" scoped>
.days {
  grid-area: 4 / 1 / 6 / 3;
  padding: 25px;
  color: #fff;
  background-color: #444444;
  border-radius: 30px;
  box-shadow: 10px 10px 4px 0px rgba(0, 0, 0, 0.50);

  &__title {
    text-align: center;
    font-size: 32px;
    font-weight: 700;
  }

  &__list {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
}

.item {
  display: flex;
  align-items: center;
  gap: 30px;

  s &__icon {
    width: 60px;
    height: 60px;
    font-weight: 600;
  }

  &__value {
    font-size: 24px;
  }

  &__date {
    font-size: 20px;
  }
}
</style>