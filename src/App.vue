<script>
export default {
  created () {
    let user = wx.getStorageSync('userinfo')
    console.log(user)
    if (!user) {
      console.log(111)
      wx.redirectTo({
        url: 'pages/userinfo/main'
      })
    }

    console.log('小程序启动成功')
  }
}
</script>

<style>

</style>
