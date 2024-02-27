<template>
  <form class="form" @submit.prevent>
    <div class="form__checkbox"></div>
    <input class="form__search" type="text" placeholder="Search your city" v-model="city">
    <button class="form__submit" ><img class="submit__icon" src="@/assets/location.svg">
      Search</button>
  </form>
</template>

<script>
export default{
  name:'app-header',
}
</script>

<style lang="scss" scoped>
@import './formInput.scss';
</style>