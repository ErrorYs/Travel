<template>
  <div class="warpper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item in swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  data () {
    return {
      swiperList: [
        {
          id: '001',
          imgUrl:
            'http://img1.qunarzz.com/piao/fusion/1812/d6/daa880b254940402.jpg_750x200_b114308a.jpg'
        },
        {
          id: '002',
          imgUrl:
            'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20191/a5379fa4391437e3c111d17e59ed24d3.jpg_750x200_3126a045.jpg'
        },
        {
          id: '003',
          imgUrl:
            'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20191/3921acb51460dc6fa9e3c7464fac5cbb.jpg_750x200_d992573a.jpg'
        }
      ],
      swiperOption: {
        pagination: '.swiper-pagination'
      }
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
  padding-bottom: 37.5%;
  overflow: hidden;
  .swiper-img {
    width: 100%;
  }
}
</style>
