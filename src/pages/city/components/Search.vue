<template>
  <div>
    <div class="search">
      <input
        type="text"
        placeholder="输入城市名或拼音"
        class="search-input"
        v-model="keyword"
      >
    </div>
    <div
      class="search-content "
      v-show="keyword"
      ref="search"
    >
      <ul>
        <li
          class="search-item border-bottom"
          v-for="item in list"
          :key="item.id"
        > {{item.name}} </li>
      </ul>
      <li
        class="search-item border-bottom"
        v-show="hasNoData"
      >没有匹配的城市</li>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      timer: null,
      list: []
    }
  },
  computed: {
    hasNoData () {
      let flag = this.list.length <= 0
      return flag
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        if (!this.keyword) {
          this.list = []
          return this.list
        }
        for (let i in this.cities) {
          this.cities[i].forEach(item => {
            if (item.spell.indexOf(this.keyword) > -1 || item.name.indexOf(this.keyword) > -1) {
              result.push(item)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang="less" scoped>
@import "~styles/varibles.less";
.search {
  height: 0.32rem;
  padding: 0.05rem;
  background-color: @bgColor;
  .search-input {
    width: 100%;
    box-sizing: border-box;
    height: 0.3rem;
    border-radius: 0.03rem;
    // text-indent: .1rem;
    padding: 0.011rem 0;
    font-size: 0.16px;
    line-height: 0.3rem;
    text-align: center;
  }
}
.search-content {
  position: absolute;
  top: 0.86rem;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: #fff;
  z-index: 1;
  overflow: hidden;
  .search-item {
    line-height: 0.31rem;
    padding-left: 0.1rem;
    background-color: #fff;
    color: #666;
  }
}
</style>
