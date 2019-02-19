<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li
        class="item"
        v-for="(item, index) in list"
        :key="index"
      >
        <div class="img-container">
          <img
            class="item-img"
            :src="item.imgUrl"
            alt=""
          >
        </div>
        <div class="item-info">
          <h3 class="item-title"> {{item.title}} </h3>
          <p class="item-desc"> {{item.desc}} </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    list: Array
  }
}
</script>

<style lang="less" scoped>
@import "~styles/mixins.less";
.title {
  // width: 100%;
  height: 0.4rem;
  background-color: #eee;
  line-height: 0.4rem;
  text-indent: 0.1rem;
  font-weight: bold;
}
.item {
  .img-container {
    height: 0;
    padding-bottom: 37.8%;
    overflow: hidden;
    .item-img {
      width: 100%;
    }
  }
  .item-info {
    padding: 0.05rem;
    min-width: 0;
    .item-title {
      line-height: 0.25rem;
      font-weight: bold;
      .ellipsis();
    }
    .item-desc {
      line-height: 0.2rem;
      color: #cccccc;
      .ellipsis();
    }
  }
}
</style>
