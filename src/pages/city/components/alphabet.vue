<template>
  <ul class="list">
    <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li>
    <li class="item">A</li>
  </ul>
</template>

<style lang="less" scoped>
@import "~styles/varibles.less";
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  right: 0;
  top:.86rem;
  bottom:0rem;
  width: .2rem;
  .item {
    width: 0.2rem;
    color: @bgColor;
    text-align: center;
    line-height: .2rem;
  }
}
</style>
