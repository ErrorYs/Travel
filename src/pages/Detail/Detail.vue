<template>
  <div>
    <detail-banner></detail-banner>
    <detail-header></detail-header>
    <div class="conten"></div>
  </div>
</template>
<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'

export default {
  name: 'detail',
  components: {
    DetailBanner,
    DetailHeader
  }
}
</script>
<style scoped>
.conten {
  height: 50rem;
}
</style>
