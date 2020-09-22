<template>
    <div>
        <detail-banner :sightName="sightName" :bannerImg="bannerImg" :bannerImgs="gallaryImgs"></detail-banner>
        <detail-header></detail-header>
        <detail-list :list="list"></detail-list>
        <div class="content"></div>
    </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
      DetailBanner,
      DetailHeader,
      DetailList
  },
  data () {
      return {
          sightName: '',
          bannerImg: '',
          gallaryImgs: [],
          list: []
      }
  },
  methods: {
      getDetailInfo () {
          axios.get('/api/detail.json?id=' + this.$route.params.id).then(this.getDetailInfoSucc)
      },
      getDetailInfoSucc (res) {
          res = res.data
          // console.log(res.data)
          // console.log(res.ret)
          if (res.ret && res.data) {
              this.sightName = res.data.sightName
              this.bannerImg = res.data.bannerImg
              this.gallaryImgs = res.data.gallaryImgs
              this.list = res.data.categoryList
          }
      }
  },
  mounted () {
      this.getDetailInfo()
  }
}
</script>

<style scoped>
    .content {
        height: 50rem;
    }
</style>
