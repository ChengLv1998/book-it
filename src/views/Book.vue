<template>
  <div class="box">
    <div class="box-left">
      <TopBar
        :src="left.src"
        :title="left.title"
        :today="left.today"
        :icon1="left.icon1"
        :icon2="left.icon2"
      ></TopBar>
      <BookTable :dataList="dataList" :timeArr="timeArr" @setTime="setTime"></BookTable>
    </div>
    <div class="box-right">
      <BookIt
        @book="bookIt"
        :src="right.src"
        :day="right.day"
        :time="right.time"
        :title="right.title"
      ></BookIt>
    </div>
  </div>
</template>

<script>
import TopBar from '../components/TopBar.vue';
import BookTable from '../components/BookTable.vue';
import BookIt from '../components/BookIt.vue';
import {TIME_ARRAY} from '../mock/data'

export default {
  components: {
    TopBar,
    BookTable,
    BookIt,
  },
  data() {
    return {
      time: '',
      left: {
        src: '/picture/16.jpg',
        title: 'Book a trip back to the future',
        today: 'TODAY',
        icon1: 'fa-angle-left',
        icon2: 'fa-angle-right',
      },
      dataList: [
        { data: ' ' },
        { data: 'Sun 6/10' },
        { data: 'Mon 6/11' },
        { data: 'Tue 6/12' },
        { data: 'Wed 6/13' },
        { data: 'Thu 6/14' },
        { data: 'Fri 6/15' },
        { data: 'Sat 6/16' },
      ],
      timeArr: TIME_ARRAY,
      right: {
        src: '/picture/16.jpg',
        day: 'June 11,2018',
        time: '10:30am-11:00am',
        title: 'Doc Brown',
      },
    };
  },
  methods: {
    setTime(time) {
      this.time = time;
    },
    async bookIt(name, email, comment) {
       alert('提交信息：name=' + name+
        ',email=' + email+
        ',comment=' + comment+
        ',time=' + this.time)
    },
  },
};
</script>

<style lang="scss" scope>
.box {
  display: flex;
  margin-top: 150px;
  .box-left {
    box-shadow: 4px 3px 4px 1px #ddd;
    border-radius: 8px;
    background-color: #f2f0f0;
    margin-right: 100px;
    margin-left: 100px;
  }
  .box-right {
    width: 300px;
    height: 600px;
    border-radius: 8px;
    background-color: #f2f0f0;
    box-shadow: 4px 3px 4px 1px #ddd;
  }
}
</style>
