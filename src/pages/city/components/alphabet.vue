<template>
  <ul class="list">
    <li
      class="item"
      v-for="(item, key) in cities"
      :key="key"
    > {{key}} </li>
  </ul>
</template>
<script>
export default {
  props: {
    cities: Object
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
