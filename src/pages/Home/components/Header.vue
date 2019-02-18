<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩
    </div>
    <div class="header-right">
      上海
      <span class="iconfont">&#xe62d;</span>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less" scoped>
@import "~styles/varibles.less";
.header {
  display: flex;
  height: 0.44rem;
  line-height: 0.44rem;
  background-color: @bgColor;
  color: #fff;
  .header-left {
    float: left;
    width: 0.42rem;
    text-align: center;
  }
  .header-input {
    flex: 1;
    border-radius: 0.1rem;
    background-color: #fff;
    line-height: 0.32rem;
    height: 0.32rem;
    margin-top: 0.06rem;
    text-indent: 0.1rem;
    color: #ccc;
  }
  .header-right {
    float: right;
    width: 0.62rem;
    text-align: center;
    span {
      font-size: 0.12rem;
    }
  }
}
</style>
