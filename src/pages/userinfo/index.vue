<template>
  <div class="container">
    <button open-type="getUserInfo">点击授权</button>
  </div>
</template>

<script>

export default {
  data () {},

  methods: {},

  created () {
    // 查看是否授权
    wx.getSetting({
      success: function (res) {
        if (res.authSetting['scope.userInfo']) {
          // 已经授权，可以直接调用 getUserInfo 获取头像昵称
          wx.getUserInfo({
            success: function (res) {
              wx.setStorageSync('userinfo', res.userInfo)
              wx.redirectTo({
                url: '/pages/me/main'
              })
            }
          })
        }
      }
    })
  }
}
</script>

<style lang='scss'>

</style>
