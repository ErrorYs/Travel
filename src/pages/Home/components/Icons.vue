<template>
  <div class="icons">
    <swiper
      class="iconSwiper-containers"
      :options="swiperOption"
    >
      <swiper-slide
        v-for="(page, index) in pages"
        :key="index"
      >
        <div
          class="icon"
          v-for="(item, index) in page"
          :key="index"
        >
          <div class="icon-img">
            <img
              class="icom-img-content"
              :src="item.imgUrl"
              alt
            >
          </div>
          <p class="icon-desc">{{ item.desc }}</p>
        </div>
      </swiper-slide>
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
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="less">
.icons {
  .iconSwiper-containers {
    padding-bottom: 50%;
  }
}
</style>

<style lang="less" scoped>
@import "~styles/mixins.less";
.icons {
  // width: 100%;
  padding-bottom: 50%;
  height: 0;
  overflow: hidden;
  background-color: #fff;
  .icon {
    position: relative;
    width: 25%;
    height: 0;
    padding-bottom: 25%;
    float: left;
    .icon-img {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.4rem;
      box-sizing: border-box;
      .icom-img-content {
        display: block;
        height: 100%;
        margin: 0.1rem auto 0;
      }
    }
    .icon-desc {
      position: absolute;
      line-height: 0.4rem;
      bottom: 0;
      left: 0;
      right: 0;
      height: 0.4rem;
      text-align: center;
      .ellipsis();
    }
  }
}
</style>
