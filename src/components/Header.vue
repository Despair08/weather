<template>
  <div class="header">
    <div class="header__checkbox"></div>
    <input type="text" class="header__search" placeholder="Search your city">
    <button class="header__submit"><img class="submit__icon" src="@/assets/location.svg"> Search</button>
  </div>
</template>

<script>
export default {
  name: 'app-header',
}
</script>

<style lang="scss">
.header {
  grid-area: 1 / 1 / 2 / 8;
  height: 60px;
  margin-top: 45px;
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
</style>.