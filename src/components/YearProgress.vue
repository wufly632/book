<template>
    <div class="progressbar">
        <progress :percent='percent' activeColor='#EA5A49'></progress>
        <p>{{year}}已经过去了{{days}}天，{{percent}}%</p>
    </div>
</template>
<script>
export default {
  methods: {
    isLeapYear () {
      const year = new Date().getFullYear()
      if (year % 400 === 0) {
        return true
      } else if (year % 4 === 0 && year % 100 !== 0) {
        return true
      } else {
        return false
      }
    },
    getDayOfYear () {
      return this.isLeapYear() ? 366 : 365
    }
  },
  computed: {
    year () {
      return new Date().getFullYear()
    },
    days () {
      let start = new Date()
      start.setMonth(0)
      start.setDate(1)
      let offset = new Date().getTime() - start.getTime()
      return parseInt(offset / 1000 / 3600 / 24) + 1
    },
    percent () {
      return (this.days / this.getDayOfYear() * 100).toFixed(1)
    }
  }
}
</script>
<style lang="scss">
.progressbar{
	width: 100%;
	progress {
		margin-bottom: 20rpx;
	}
}
</style>

