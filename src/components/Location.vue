<template>
  <div class="location">
    <h2 class="location__city"> {{ cityName }} </h2>
    <p class="location__time">{{ time }}</p>
    <p class="location__date">{{ date }}</p>
  </div>
</template>

<script>
export default {
  name: 'app-location',
  props: {
    city: String
  },
  data() {
    return {
      cityName: this.city,
      date: null,
      time: null,
      monthNames: [`Jan`, `Feb`, `March`, `Apr`, `May`, `Jun`, `Jul`, `Aug`, `Sep`, `Oct`, `Nov`, `Dec`],
      dayNames: ['Monday', 'Thursday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
    }
  },
  methods: {
    getTime() {
      setInterval(() => {
        const date = new Date();
        let minutes, hours;
        date.getMinutes() < 10 ? minutes = '0' + date.getMinutes() : minutes = date.getMinutes();
        date.getHours() < 10 ? hours = '0' + date.getHours() : hours = date.getHours();
        return this.time = `${hours}:${minutes}`;
      }, 1000);
    }
  },
  mounted() {
    this.getTime()
  },
  created() {
    const date = new Date();
    this.date = `${this.dayNames[date.getDay()]}, ${date.getDate()} ${this.monthNames[date.getMonth()]}`;
  }
}
</script>

<style lang="scss" scoped>
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
  user-select: none;

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