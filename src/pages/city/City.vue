<template>
  <div>
    <Header></Header>
    <city-search></city-search>
  </div>
</template>

<script>
import Header from './components/Header'
import CitySearch from './components/Search'
export default {
  components: {
    Header,
    CitySearch
  }
}
</script>
