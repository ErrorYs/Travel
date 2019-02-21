<template>
  <ul class="list">
    <li
      class="item"
      v-for="item in letters"
      :key="item"
      :ref="item"
      @click="handleLetterClick"
      @touchstart="handeltouchstart"
      @touchmove="handeltouchmove"
      @touchend="handeltouchend"
    > {{item}} </li>
  </ul>
</template>
<script>
export default {
  props: {
    cities: Object
  },
  data () {
    return {
      touchstatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handeltouchstart () {
      this.touchstatus = true
    },
    handeltouchmove (e) {
      if (this.touchstatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 86
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handeltouchend () {
      this.touchstatus = false
    }
  },
  computed: {
    letters () {
      const letters = []
      for (const key in this.cities) {
        letters.push(key)
      }
      return letters
    }
  }
}
</script>
<style lang="less" scoped>
@import "~styles/varibles.less";
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  right: 0;
  top: 0.86rem;
  bottom: 0rem;
  width: 0.2rem;
  .item {
    width: 0.2rem;
    color: @bgColor;
    text-align: center;
    line-height: 0.2rem;
  }
}
</style>
