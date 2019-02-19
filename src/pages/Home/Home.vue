<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <Recommend></Recommend>
    <Weenkend></Weenkend>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import Recommend from './components/Recommend'
import Weenkend from './components/Weekend'
export default {
  name: 'Home',
  components: {
    HomeHeader: HomeHeader,
    HomeSwiper,
    HomeIcons,
    Recommend,
    Weenkend
  }
}
</script>

<style lang='less' scoped>
</style>
