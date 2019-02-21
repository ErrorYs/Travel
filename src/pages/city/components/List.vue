<template>
  <div
    class="list"
    ref="wrapper"
  >
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-lsit">
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-lsit">
          <div
            class="button-warpper"
            v-for="item in hotCities"
            :key="item.id"
          >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div
        class="area"
        v-for="(item, key) in cities"
        :key="key"
        :ref="key"
      >
        <div class="title border-topbottom"> {{key}} </div>
        <div class="item-list">
          <div
            class="item border-bottom"
            v-for="innerItem in item"
            :key="innerItem.id"
          > {{innerItem.name}} </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
  name: 'cityList',
  props: {
    cities: Object,
    hotCities: Array,
    cityAlphabet: String
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    cityAlphabet () {
      // console.log(this.cityAlphabet)
      if (this.cityAlphabet) {
        const letter = this.$refs[this.cityAlphabet][0]
        this.scroll.scrollToElement(letter)
      }
    }
  }
}
</script>
<style lang="less" scoped>
.list {
  position: absolute;
  top: 0.86rem;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
  .area {
    .item-list {
      .item {
        line-height: 0.32rem;
        color: #666;
        padding-left: 0.1rem;
      }
    }
    .title {
      background-color: #eee;
      height: 0.3rem;
      line-height: 0.3rem;
      padding-left: 0.1rem;
      color: #666;
    }
    .button-lsit {
      overflow: hidden;
      padding: 0.05rem 0.3rem 0.05rem 0.05rem;
      .button-warpper {
        width: 33.33%;
        float: left;
        .button {
          padding: 0.05rem 0;
          margin: 0.02rem;
          border: 0.01rem solid #ccc;
          border-radius: 0.03rem;
          text-align: center;
        }
      }
    }
  }
  .border-topbottom {
    &::before {
      border-color: #ccc;
    }
    &::after {
      border-color: #ccc;
    }
  }
  .border-bottom {
    &::before {
      border-color: #ccc;
    }
    &::after {
      border-color: #ccc;
    }
  }
}
</style>
