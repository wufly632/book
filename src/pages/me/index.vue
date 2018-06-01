<template>
  <div class="container">
    <div class="userinfo">
      <img :src="userinfo.avatarUrl" alt="">
      <p>{{userinfo.nickName}}</p>
    </div>
    <YearProgress></YearProgress>
    <button class="btn" @click="scanBook">添加图书</button>
  </div>
</template>

<script>
import YearProgress from '@/components/YearProgress'
export default {
  data () {
    return {
      userinfo: {}
    }
  },
  components: {
    YearProgress
  },
  methods: {
    scanBook () {
      wx.scanCode({
        success: (res) => {
          console.log(15)
          console.log(res)
        }
      })
    }
  },

  created () {
    this.userinfo = wx.getStorageSync('userinfo')
    console.log(this.userinfo)
  }
}
</script>

<style lang='scss'>
.container{
  padding:0 30rpx;
}
.userinfo{
  margin-top:100rpx;
  text-align: center;
  img{
    width: 300rpx;
    height: 300rpx;
    margin: 20rpx;
  }
  p{
    margin: 20rpx;
  }
}
</style>
