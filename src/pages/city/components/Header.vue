<template>
  <div class="header">
    城市选择
    <router-link
      to="/"
      class="back-home"
    >
      <span class="iconfont">&#xe624;</span>
    </router-link>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="less" scoped>
@import "~styles/varibles.less";
.header {
  position: relative;
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
