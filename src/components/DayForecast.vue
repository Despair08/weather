<template>
  <div class="days">
    <h3 class="days__title">Days forecast:</h3>
    <ul class="days__list">
      <li class="days__item item">
        <img src="@/assets/clouds--temp.svg" alt="day icon" class="item__icon">
        <span class="item__value">20&deg;C</span>
        <span class="item__date">Friday, 1 Sep</span>
      </li>
      <li class="days__item item">
        <img src="@/assets/clouds--temp.svg" alt="day icon" class="item__icon">
        <span class="item__value">20&deg;C</span>
        <span class="item__date">Friday, 1 Sep</span>
      </li>
      <li class="days__item item">
        <img src="@/assets/clouds--temp.svg" alt="day icon" class="item__icon">
        <span class="item__value">20&deg;C</span>
        <span class="item__date">Friday, 1 Sep</span>
      </li>
      <li class="days__item item">
        <img src="@/assets/clouds--temp.svg" alt="day icon" class="item__icon">
        <span class="item__value">20&deg;C</span>
        <span class="item__date">Friday, 1 Sep</span>
      </li>
      <li class="days__item item">
        <img src="@/assets/clouds--temp.svg" alt="day icon" class="item__icon">
        <span class="item__value">20&deg;C</span>
        <span class="item__date">Friday, 1 Sep</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'day-forecast'
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
    align-items: center;
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