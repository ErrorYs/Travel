<template>
  <div
    class="container"
    @click="handleClickGallery"
  >
    <div class="warpper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide
          v-for="(item, index) in imgs"
          :key="index"
        >
          <img
            class="swiper-img"
            :src="item"
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
  </div>
</template>
<script>
export default {
  props: {
    imgs: {
      type: Array
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleClickGallery () {
      this.$emit('galleryClose')
    }
  }
}
</script>

<style lang="less" scoped>
.swiper-container {
  overflow: inherit;
}
</style>

<style lang="less" scoped>
.container {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  background-color: #000;
  display: flex;
  justify-content: center;
  flex-direction: column;
  z-index: 99;
  .warpper {
    width: 100%;
    height: 0;
    padding-bottom: 100%;
  }
  .swiper-img {
    width: 100%;
  }
  .swiper-pagination {
    bottom: -1rem;
    color: #fff;
  }
}
</style>
