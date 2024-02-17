<template>
  <div class="days"></div>
</template>

<script>
export default {
  name: 'day-forecast'
}
</script>

<style lang="scss">
.days {
  grid-area: 4 / 1 / 6 / 3;
  color: #fff;
  background-color: #444444;
  border-radius: 30px;
  box-shadow: 10px 10px 4px 0px rgba(0, 0, 0, 0.50);
}
</style>