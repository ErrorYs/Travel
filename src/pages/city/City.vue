<template>
  <div>
    <Header></Header>
    <city-search></city-search>
    <city-list
      :cities="cities"
      :hotCities="hotcities"
      :cityAlphabet="cityAlphabet"
    ></city-list>
    <city-alphabet
      :cities="cities"
      @change="getalphaabet"
    ></city-alphabet>
  </div>
</template>

<script>
import Header from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/alphabet'
import axios from 'axios'
export default {
  components: {
    Header,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotcities: [],
      cityAlphabet: ''
    }
  },
  methods: {
    getCityinfo () {
      axios.get('api/city.json').then(this.getCityinfoSucc)
    },
    getCityinfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.cities = data.cities
        this.hotcities = data.hotCities
      }
    },
    getalphaabet (data) {
      this.cityAlphabet = data
    }
  },
  mounted () {
    this.getCityinfo()
  }
}
</script>
