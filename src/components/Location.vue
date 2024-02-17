<template>
  <div class="location">
    <h2 class="location__city"> city </h2>
    <p class="location__time">09:00</p>
    <p class="location__date">Saturday, 17 Feb</p>
  </div>
</template>

<script>
export default {
  name: 'app-location'
}
</script>

<style lang="scss">
.location {
  grid-area: 2 / 1 / 4 / 4;
  display: flex;
  flex-direction: column;
  padding: 50px 105px 40px;
  align-items: center;
  color: #fff;
  background-color: #444444;
  border-radius: 30px;
  box-shadow: 10px 10px 4px 0px rgba(0, 0, 0, 0.50);

  &__city {
    font-size: 36px;
    font-weight: 700;
  }

  &__time {
    padding-top: 10px;
    font-size: 96px;
    font-weight: 700;
  }

  &__date {
    font-size: 20px;
  }
}
</style>