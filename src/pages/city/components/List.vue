<template>
  <div
    class="list"
    ref="wrapper"
  >
    <div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-lsit">
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">字母排序</div>
        <div class="button-lsit">
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
          <div class="button-warpper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">A</div>
        <div class="item-list">
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">A</div>
        <div class="item-list">
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">A</div>
        <div class="item-list">
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">A</div>
        <div class="item-list">
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
          <div class="item border-bottom">重庆</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
  name: 'cityList',
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
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
