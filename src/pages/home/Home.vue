<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :icons="iconList"></home-icons>
    <home-recommend :recommend="recommendList"></home-recommend>
    <home-weekend :weekend="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import Vuex from 'vuex'

import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.$store.state.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      // console.log(res.ret)
      if (res.ret && res.data) {
        this.swiperList = res.data.swiperList
        this.iconList = res.data.iconList
        this.recommendList = res.data.recommendList
        this.weekendList = res.data.weekendList
      }
    }
  },
  mounted () {
    this.getHomeInfo()
    this.lastCity = this.$store.state.city
  },
  activated () {
    if (this.lastCity !== this.$store.state.city) {
      this.getHomeInfo()
      this.lastCity = this.$store.state.city
    }
  }
}
</script>

<style>

</style>
