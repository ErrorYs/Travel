<template>
  <div>
    <div
      class="banner"
      @click="handleGalleryclick"
    >
      <img
        src="//img1.qunarzz.com/sight/p0/1709/e4/e4b97c2fbb4e696a3.img.png_600x330_d421ab3d.png"
        class="banner-img"
        alt=""
      >
      <div class="banner-info">
        <div class="banner-title">濯水景区-蒲花暗河</div>
        <div class="banner-number">
          <span class="iconfont">&#xe632;</span>
          39
        </div>
      </div>
    </div>
    <detail-gallery
      :imgs="imgs"
      v-show="showGallery"
      @galleryClose="handleGalleryClose"
    ></detail-gallery>
  </div>
</template>

<script>
import DetailGallery from 'common/gallery/gallery.vue'
export default {
  name: 'banner',
  data () {
    return {
      imgs: ['http://img1.qunarzz.com/sight/p0/1709/e4/e4b97c2fbb4e696a3.img.png_r_800x800_ae927025.png', 'http://img1.qunarzz.com/sight/p0/1709/39/39b5b5a87f82aac2a3.img.jpg_r_800x800_5556a76a.jpg'],
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
    DetailGallery
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
