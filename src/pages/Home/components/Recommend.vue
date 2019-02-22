<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li
        class="item"
        v-for="(item, index) in list"
        :key="index"
      >
        <img
          class="item-img"
          :src="item.imgUrl"
          alt=""
        >
        <router-link
          class="item-info"
          :key="item.id"
          :to="'/detail/'+item.id"
          tag="div"
        >
          <h3 class="item-title"> {{item.title}} </h3>
          <p class="item-desc"> {{item.desc}} </p>
          <button class="item-button">查看详情</button>
        </router-link>
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
  display: flex;
  .item-img {
    width: 0.85rem;
    height: 0.85rem;
    padding: 0.05rem;
  }
  .item-info {
    flex: 1;
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
    .item-button {
      // width: .75rem;
      // height: .2rem;
      background-color: #ff9300;
      border-radius: 0.03rem;
      margin-top: 0.1rem;
      color: #fff;
      line-height: 0.2rem;
      font-size: 0.12rem;
      padding: 0 0.1rem;
    }
  }
}
</style>
