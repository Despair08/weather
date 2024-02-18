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
  max-width: 1390px;
  margin: 0 auto;
  padding: 20px 15px 0;
  display: grid;
  grid-template-columns: repeat(7);
  grid-template-rows: repeat(5);
  grid-column-gap: 45px;
  grid-row-gap: 45px;
}

.header {
  grid-area: 1 / 1 / 2 / 8;
  height: 60px;
  display: flex;
  justify-content: space-between;
  gap: 20px;

  &__checkbox {
    width: 110px;
  }

  &__search {
    width: 800px;
    padding: 10px 20px;
    background-color: #444;
    border: none;
    border-radius: 40px;
    font-size: 18px;
    color: #fff;
    box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.20);

    &:focus,
    &:active {
      outline: none;
    }
  }

  &__submit {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 10px;
    gap: 20px;
    width: 292px;
    border: none;
    border-radius: 40px;
    font-size: 22px;
    font-weight: 700;
    color: #fff;
    background-color: #4CBB17;
    cursor: pointer;
    transition: .3s ease;

    &:hover {
      background-color: #3eaa16;
      transition: background-color .3s ease;
    }

    &:active {
      transform: translateY(3px);
      transition: transform .3s ease;
    }
  }
}
</style>