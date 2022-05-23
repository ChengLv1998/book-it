<template>
  <div class="it">
    <img :src="src" alt="" />
    <div class="colse">
      <span class="fa fa-close"></span>
    </div>
    <div class="mid">
      <div class="day">{{ day }}</div>
      <div class="time">{{ time }}</div>
      <div class="with">with</div>
      <div class="title">{{ title }}</div>
    </div>
    <div class="msg">
      <input v-model="name" class="name input" type="text" placeholder="Name" />
      <input v-model="email" class="email input" type="text" placeholder="E-mail" />
      <textarea v-model="comment" class="comment input" placeholder="Comment"></textarea>
    </div>
    <button class="button" @click="bookIt">BOOK IT</button>
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      default: '/picture/16.jpg',
    },
    day: {
      type: String,
      default: 'June 11,2018',
    },
    time: {
      type: String,
      default: '10:30am-11:00am',
    },
    title: {
      type: String,
      default: 'Doc Brown',
    },
  },
  data() {
    return {
      name:'',
      email:'',
      comment:'',
    }
  },
  methods: {
    bookIt(){
      console.log('vgdhj')
      this.$emit('book', this.name,this.email,this.comment)
    },

    // bookIt:function(){
      
    //   console.log("用户所填信息 name="+this.name+
    //   ",email="+this.email+",comment="+this.comment);
    //   alert('已提交')
    // }
  },
};
</script>

<style lang="scss" scope>
.it {
  position: relative;
  img {
    position: absolute;
    width: 60px;
    border-radius: 50%;
    left: 120px;
    top: -40px;
  }
  .colse {
    display: flex;
    flex-direction: row-reverse;
    margin: 10px;
    span {
      padding: 0 6px;
      &:hover {
        background-color: red;
        cursor: pointer;
        border-radius: 4px;
      }
    }
  }
  .mid {
    text-align: center;
    .day {
      font-size: 32px;
      color: #444;
      margin: 20px 0;
    }
    .time {
      font-size: 16px;
      color: #555;
      margin: 20px 0;
    }
    .with {
      font-size: 12px;
      color: #888;
      margin: 20px 0;
    }
    .title {
      font-size: 16px;
      color: #555;
      margin: 20px 0;
    }
  }
  .msg {
    display: flex;
    flex-direction: column;
    .input {
      width: 90%;
      margin: auto;
      border: 1px solid #dfdfdf;
      border-radius: 4px;
      padding-left: 10px;
    }
    .name,
    .email {
      height: 60px;
    }
    .comment {
      height: 80px;
      padding-top: 10px;
    }
  }
  .button {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(52, 104, 201);
    margin: auto;
    width: 100px;
    height: 40px;
    border-radius: 4px;
    margin-top: 50px;
    color: #fff;
    &:hover {
      cursor: pointer;
    }
  }
}
</style>
