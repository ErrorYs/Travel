<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item" v-for="(item, index) in recommontList" :key="index">
        <img
          class="item-img"
          :src="item.imgUrl"
          alt=""
        >
        <div class="item-info">
          <h3 class="item-title"> {{item.title}} </h3>
          <p class="item-desc"> {{item.desc}} </p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      recommontList: [
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_200x200_9a7794fc.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/p0/1603/17/170481fb9caf500790.water.jpg_200x200_a32b9a92.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/tuan/team2/1507/2c/83e0e0e7ae082a.jpg_200x200_6d7378b2.jpg' }
      ]
    }
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
