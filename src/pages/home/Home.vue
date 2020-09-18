<template>
  <div>
    <HomeHeader :city="city"></HomeHeader>
    <HomeSwiper :list="swiperList"></HomeSwiper>
    <HomeIcons :icons="iconList"></HomeIcons>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'

import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons
  },
  data () {
    return {
      city: '',
      swiperList: [],
      iconList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      console.log(res)
      if (res.ret && res.data) {
        this.city = res.data.city
        this.swiperList = res.data.swiperList
        this.iconList = res.data.iconList
      }
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style>

</style>
