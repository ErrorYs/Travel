<template>
  <div>
    <router-link
      tag="div"
      to="/"
      class="header-abs"
      v-show="showAbs"
    >
      <span class="iconfont">&#xe624;</span>
    </router-link>
    <div
      class="header-fixed"
      v-show="!showAbs"
      v-bind:style="styleObject"
    >
      城市选择
      <router-link
        to="/"
        class="back-home"
      >
        <span class="iconfont">&#xe624;</span>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      styleObject: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 40) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.styleObject = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="less" scoped>
@import "~styles/varibles.less";
.header-abs {
  position: absolute;
  top: 0.1rem;
  left: 0.1rem;
  width: 0.4rem;
  height: 0.4rem;
  background-color: rgba(0, 0, 0, 0.8);
  text-align: center;
  line-height: 0.4rem;
  color: #fff;
  border-radius: 50%;
}
.header-fixed {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 0.44rem;
  line-height: 0.44rem;
  text-align: center;
  color: #fff;
  background: @bgColor;
  font-size: 16px;
  .back-home {
    color: #fff;
    position: absolute;
    left: 0.1rem;
    top: 0;
  }
}
</style>
