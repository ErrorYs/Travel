<template>
  <div>
    <Header></Header>
    <city-search></city-search>
    <city-list></city-list>
    <city-alphabet></city-alphabet>
  </div>
</template>

<script>
import Header from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/alphabet'
export default {
  components: {
    Header,
    CitySearch,
    CityList,
    CityAlphabet
  }
}
</script>
