<template>
  <div class="table">
    <div class="dayList">
      <div class="day" v-for="(item, index1) in dataList" :key="'a' + index1">{{ item.data }}</div>
    </div>
    <div class="scroll">
      <div class="timeArr" v-for="(n, index2) in timeArr" :key="'a' + index2">
        <div class="item-box" v-for="(i, index3) in n.timeList" :key="'b' + index3">
          <span
            class="time"
            :class="i.isShow ? 'has-border' : ''"
            @click="clickMe($event, i.time, dataList[index3].data, i.isShow)"
          >
            {{ i.isShow ? i.time : '' }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    dataList: {
      type: Array,
      default: function () {
        return [
          { data: ' ' },
          { data: 'Sun 6/10' },
          { data: 'Mon 6/11' },
          { data: 'Tue 6/12' },
          { data: 'Wed 6/13' },
          { data: 'Thu 6/14' },
          { data: 'Fri 6/15' },
          { data: 'Sat 6/16' },
        ];
      },
    },
    timeArr: {
      type: Array,
      default: function () {
        return [
          {
            timeList: [
              { time: '9:30am' },
              { time: ' ' },
              { time: ' ' },
              { time: ' ' },
              { time: ' ' },
              { time: ' ' },
              { time: ' ' },
              { time: ' ' },
            ],
          },
        ];
      },
    },
  },
  data() {
    return {
      isSelected: false,
    };
  },
  methods: {
    clickMe(event, time, day, isShow) {
      if (isShow) {
        if (this.isSelected) {
          event.currentTarget.className = 'time has-border';
          this.isSelected = false;
        } else {
          event.currentTarget.className = 'time has-border selected';
          this.isSelected = true;
        }
        this.$emit('setTime', time + ' ' + day);
      }
    },
  },
};
</script>

<style lang="scss" scop>
.table {
  .dayList {
    display: flex;
    .day {
      width: 80px;
      height: 30px;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 2px 4px;
      border-right: 1px solid #dfdfdf;
      border-bottom: 1px solid #dfdfdf;
      border-top: 1px solid #dfdfdf;
      color: #999;
      font-size: 14px;
    }
  }
  .scroll {
    overflow-y: auto;
    height: 514px;
    .timeArr {
      display: flex;
      &:last-child {
        .item-box {
          &:first-child {
            border-bottom: 0;
          }
        }
      }
      .item-box {
        border-right: 1px solid #dfdfdf;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 4px;
        &:first-child {
          border-bottom: 1px solid #dfdfdf;
          .time {
            border-left: 0;
            background-color: #f2f0f0;
            border-radius: 0;
            color: #999;
          }
        }
        .time {
          display: flex;
          justify-content: center;
          align-items: center;
          box-sizing: border-box;
          width: 80px;
          height: 40px;
          color: #777;
          font-size: 14px;
        }
        .has-border {
          border-left: 2px solid #777;
          background-color: #fff;
          border-radius: 4px;
        }
        .selected {
          color: blue;
          border-color: blue;
        }
      }
    }
  }
}
</style>
