<template>
  <div class="search">
    <input type="text" placeholder="输入城市名或拼音" class="search-input">
  </div>
</template>

<script>
export default {

}
</script>

<style lang="less" scoped>
@import "~styles/varibles.less";
.search {
  height: .32rem;
  padding: .05rem;
  background-color: @bgColor;
  .search-input {
    width: 100%;
    box-sizing: border-box;
    height: 0.3rem;
    border-radius: .03rem;
    // text-indent: .1rem;
    padding: .011rem 0;
    font-size: .16px;
    line-height: .3rem;
    text-align: center
  }
}
</style>
