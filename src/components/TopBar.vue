<template>
  <div class="top-bar">
    <img :src="src" alt="" />
    <div class="bar-left">{{ title }}</div>
    <div class="bar-right">
      <i>{{ today }}</i>
      <i class="fa" :class="icon1"></i>
      <i class="fa" :class="icon2"></i>
      <i></i>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      default: '/picture/16.jpg',
    },
    title: {
      type: String,
      default: 'Book a trip back to the future',
    },
    today: {
      type: String,
      default: 'TODAY',
    },
    icon1: {
      type: String,
      default: 'fa-angle-left',
    },
    icon2: {
      type: String,
      default: 'fa-angle-right',
    },
  },
};
</script>

<style lang="scss" scope>
.top-bar {
  position: relative;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 10px;
  padding-right: 10px;
  img {
    position: absolute;
    left: 314px;
    top: -40px;
    width: 80px;
    border-radius: 50%;
  }
  .bar-left {
    margin-left: 20px;
  }
  .bar-right {
    color: #999;
    i {
      margin-left: 30px;
    }
  }
}
</style>
