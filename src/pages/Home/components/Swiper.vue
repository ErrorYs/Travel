<template>
  <div class="warpper">
    <swiper
      :options="swiperOption"
      v-if="showSwiper"
    >
      <!-- slides -->
      <swiper-slide
        v-for="item in list"
        :key="item.id"
      >
        <img
          class="swiper-img"
          :src="item.imgUrl"
          alt
        >
      </swiper-slide>
      <!-- Optional controls -->
      <div
        class="swiper-pagination"
        slot="pagination"
      ></div>
    </swiper>
  </div>
</template>

<script>
export default {
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 2000
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }

}

</script>

<style lang="less">
.warpper {
  .swiper-pagination-bullet-active {
    background-color: #fff;
  }
}
</style>

<style lang="less" scoped>
.warpper {
  width: 100%;
  height: 0;
  padding-bottom: 31.25%;
  overflow: hidden;
  .swiper-img {
    width: 100%;
  }
}
</style>
