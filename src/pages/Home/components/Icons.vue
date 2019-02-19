<template>
  <div class="icons">
    <swiper class="iconSwiper-containers">
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
  data () {
    return {
      iconsList: [
        {
          id: '0001',
          desc: '景点门票',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png'
        },
        {
          id: '0002',
          desc: '一日游',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png'
        },
        {
          id: '0003',
          desc: '重庆必游',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png'
        },
        {
          id: '0004',
          desc: '精品小团',
          imgUrl:
            'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20191/de711920c71e38287d9f95f7910aa1aa.png'
        },
        {
          id: '0005',
          desc: '室内场馆',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/fa/2548667cb6e902.png'
        },
        {
          id: '0006',
          desc: '两江夜游',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/89/55083b0f1951f302.png'
        },
        {
          id: '0007',
          desc: '神秘武隆',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/96/c70f1e85ae4a4f02.png'
        },
        {
          id: '0008',
          desc: '泡温泉',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png'
        },
        {
          id: '0009',
          desc: '重庆滑雪',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/fc/b10a6b2e4f0fe102.png'
        },
        {
          id: '0010',
          desc: '游乐场',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png'
        }
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconsList.forEach((item, index) => {
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
@import '~styles/mixins.less';
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
