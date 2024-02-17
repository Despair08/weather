<template>
  <div class="hours">
    <h3 class="hours__title">Hourly forecast:</h3>
    <ul class="hours__list">
      <li class="hours__item item">
        <span class="item__time">12:00</span>
        <img class="item__icon" src="@/assets/clouds--temp.svg" alt="card ico">
        <span class="item__value">20&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico">
        <span class="item__wind-value">3 m/s</span>
      </li>
      <li class="hours__item item">
        <span class="item__time">12:00</span>
        <img class="item__icon" src="@/assets/clouds--temp.svg" alt="card ico">
        <span class="item__value">20&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico">
        <span class="item__wind-value">3 m/s</span>
      </li>
      <li class="hours__item item">
        <span class="item__time">12:00</span>
        <img class="item__icon" src="@/assets/clouds--temp.svg" alt="card ico">
        <span class="item__value">20&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico">
        <span class="item__wind-value">3 m/s</span>
      </li>
      <li class="hours__item item">
        <span class="item__time">12:00</span>
        <img class="item__icon" src="@/assets/clouds--temp.svg" alt="card ico">
        <span class="item__value">20&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico">
        <span class="item__wind-value">3 m/s</span>
      </li>
      <li class="hours__item item">
        <span class="item__time">12:00</span>
        <img class="item__icon" src="@/assets/clouds--temp.svg" alt="card ico">
        <span class="item__value">20&deg;C</span>
        <img class="item__nav" src="@/assets/nav__forecast-card.svg" alt="nav ico">
        <span class="item__wind-value">3 m/s</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hour-forecast'
}
</script>

<style lang="scss" scoped>
.hours {
  grid-area: 4 / 3 / 6 / 8;
  padding: 25px;
  color: #fff;
  background-color: #444444;
  border-radius: 30px;
  box-shadow: 10px 10px 4px 0px rgba(0, 0, 0, 0.50);

  &__title {
    font-size: 32px;
    font-weight: 700;
    text-align: center;
  }

  &__list {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    gap: 15px;
  }
}

.item {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 20px 30px;
  border-radius: 40px;
  background-color: #373636;
  font-size: 20px;
  font-weight: 700;

  &__time {
    font-size: 24px;
  }

  &__icon {}

  &__value {}

  &__nav {}

  &__wind-value {}
}
</style>