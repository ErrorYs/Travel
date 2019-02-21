<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{this.city}}
        <span class="iconfont">&#xe62d;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
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
    margin-left: 0.1rem;
    padding-left: 0.2rem;
  }
  .header-right {
    float: right;
    padding: 0 0.02rem;
    min-width: 0.52rem;
    float: right;
    text-align: center;
    color: #fff;
    span {
      font-size: 0.12rem;
      margin-left: -0.02rem;
    }
  }
}
</style>
