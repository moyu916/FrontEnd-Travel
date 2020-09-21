<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/201404/23/04b92c99462687fa1ba45c1b5ba4ad77.jpg_600x330_bf9c4904.jpg" alt="">
            <div class="banner-info">
                <div class="banner-title">大连圣亚海洋世界(AAAA景区)</div>
                <div class="banner-number">
                    <span class="iconfont icon-search">&#xe6a2;</span>39
                </div>
            </div>
        </div>
        <common-gallary :imgs="imgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
    </div>
</template>

<script>
import CommonGallary from '@/common/gallary/gallary'
export default {
  name: 'DetailBanner',
  components: {
      CommonGallary
  },
  data () {
      return {
          imgs: [],
          showGallary: false
      }
  },
  methods: {
      handleBannerClick () {
          this.showGallary = true
      },
      handleGallaryClose () {
          this.showGallary = false
      }
  }
}
</script>

<style scoped>
    .banner {
        position: relative;
        /* overflow: hidden;
        height: 0;
        padding-bottom: 55%;  */
        height: 55vw;
    }
    .banner-img {
        width: 100%;
    }
    .banner-info {
       position: absolute;
       left: 0;
       right: 0;
       bottom: 0;
       line-height: .6rem;
       display: flex;
       color: #fff;
       background-image: linear-gradient(top, rgba(0,0,0,0),rgba(0,0,0,0.8));
    }
    .banner-title {
        flex: 1;
        font-size: .32rem;
        padding: 0 .2rem;
    }
    .banner-number {
        margin: .14rem 0;
        padding: 0 .24rem;
        line-height: .32rem;
        height: .32rem;
        border-radius: .2rem;
        background: rgba(0,0,0,.8);
    }

</style>