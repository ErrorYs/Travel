<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="(item, index) in recommontList" :key="index">
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
  data () {
    return {
      recommontList: [
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/source/1511/ea/7f43191b747bb9.jpg_r_640x214_f58e829d.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/source/1505/7d/df6ff468331c43.jpg_r_640x214_1f3783d0.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/source/1603/ad/69b0fc5f48ad5f.jpg_r_640x214_b0fd5c7b.jpg' },
        { id: '0001', title: '故宫', desc: '东方宫殿的代表,世界宫殿建筑典范', imgUrl: 'http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg' }
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
