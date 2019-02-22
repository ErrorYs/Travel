<template>
  <div>
    <div
      v-for="(item, index) in List"
      :key="index"
      class="item"
    >
      <div class="item-title border-bottom"> {{item.title}} </div>
      <div v-if="item.children" class="item-children">
        <detail-list :List="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    List: Array
  }
}
</script>

<style lang="less" scoped>
.item-title {
  line-height: 0.3rem;
  height: 0.3rem;
  padding: 0 0.1rem;
}
.item-children {
  padding: 0 .1rem;
}
</style>
