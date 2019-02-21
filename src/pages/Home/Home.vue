<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="SwiperList"></home-swiper>
    <home-icons :list="iconsList"></home-icons>
    <Recommend :list="RecommendList"></Recommend>
    <Weenkend :list="weekendList"></Weenkend>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import Recommend from './components/Recommend'
import Weenkend from './components/Weekend'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader: HomeHeader,
    HomeSwiper,
    HomeIcons,
    Recommend,
    Weenkend
  },
  data () {
    return {
      SwiperList: [],
      RecommendList: [],
      iconsList: [],
      weekendList: []
    }
  },
  methods: {
    getHomeinfo () {
      axios.get('api/index.json')
        .then(this.getHomeinfoSucc)
    },
    getHomeinfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.SwiperList = data.swiperList
        this.RecommendList = data.recommendList
        this.iconsList = data.iconList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted () {
    this.getHomeinfo()
  }
}
</script>

<style lang='less' scoped>
</style>
