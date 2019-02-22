<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header></detail-header>
    <detail-list :List="list"></detail-list>
    <div class="conten"></div>
  </div>
</template>
<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/LIst'

export default {
  name: 'detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      list: [
        { title: '儿童票',
          children: [
            { title: '儿童1票' },
            { title: '儿童2票' },
            { title: '儿童3票' },
            { title: '儿童4票',
              children: [
                { title: '儿童儿子1' },
                { title: '儿童儿子2' },
                { title: '儿童儿子3' },
                { title: '儿童儿子4' }
              ] }
          ] },
        { title: '成人票' },
        { title: '老人票' },
        { title: '学生票' }
      ]
    }
  }
}
</script>
<style scoped>
.conten {
  height: 50rem;
}
</style>
