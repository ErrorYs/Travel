<template>
  <div>
    <div
      class="banner"
      @click="handleGalleryclick"
    >
      <img
        :src="bannerImg"
        class="banner-img"
        alt=""
      >
      <div class="banner-info">
        <div class="banner-title"> {{sightName}} </div>
        <div class="banner-number">
          <span class="iconfont">&#xe632;</span>
          {{gallaryImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <detail-gallery
        :imgs="gallaryImgs"
        v-show="showGallery"
        @galleryClose="handleGalleryClose"
      ></detail-gallery>
    </fade-animation>
  </div>
</template>

<script>
import DetailGallery from 'common/gallery/gallery.vue'
import FadeAnimation from 'common/fade/animationFade.vue'
export default {
  name: 'banner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    handleGalleryclick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  },
  components: {
    DetailGallery,
    FadeAnimation
  }

}
</script>

<style lang="less" scoped>
.banner {
  position: relative;
  padding-bottom: 55%;
  height: 0;
  overflow: hidden;
  .banner-img {
    width: 100%;
  }
  .banner-info {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    line-height: 0.3rem;
    color: #fff;
    display: flex;
    background-image: linear-gradient(
      top,
      rgba(0, 0, 0, 0),
      rgba(0, 0, 0, 0.8)
    );
    .banner-title {
      font-size: 0.18rem;
      flex: 1;
      padding: 0 0.1rem;
    }
    .banner-number {
      font-size: 0.12rem;
      padding: 0 0.2rem;
      background-color: rgba(0, 0, 0, 0.5);
      text-align: center;
      border-radius: 0.06rem;
      line-height: 0.2rem;
      height: 0.2rem;
      margin-top: 0.05rem;
    }
  }
}
</style>
