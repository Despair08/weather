<template>
  <div class="details">
    <div class="details__temp temp">
      <p class="temp__current">24&deg;C</p>
      <p class="temp__like">Feels like:</p>
      <p class="temp__feels-like">22&deg;C</p>
    </div>
    <div class="details__descr descr">
      <img class="descr__icon" src="@/assets/clear--temp.svg" alt="weather icon">
      <p class="descr__text">Sunny</p>
    </div>
    <div class="cards cards">
      <ul class="cards__list">
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/wind--dark.svg" alt="weather_icon">
          <p class="item__value">0.2 km/h</p>
          <p class="item__descr">Wind</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/wind--dark.svg" alt="weather_icon">
          <p class="item__value">0.2 km/h</p>
          <p class="item__descr">Wind</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/wind--dark.svg" alt="weather_icon">
          <p class="item__value">0.2 km/h</p>
          <p class="item__descr">Wind</p>
        </li>
        <li class="cards__item item">
          <img class="item__icon" src="@/assets/wind--dark.svg" alt="weather_icon">
          <p class="item__value">0.2 km/h</p>
          <p class="item__descr">Wind</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app-details'
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