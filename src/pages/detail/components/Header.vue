<template>
  <div class="header">

      <router-link 
        tag="div" 
        to="/" 
        class="header-abs"
      >
        <span class="iconfont icon-arrow-left" v-show="showAbs">
            &#xe743;
        </span>
      </router-link>

      <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
        <router-link to="/">
            <span class="iconfont header-fixed-back">&#xe743;</span>
        </router-link>
          景点详情
      </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
      return {
          showAbs: true,
          opacityStyle: {
              opacity: 0
          }
      }
  },
  methods: {
      handleScroll () {
          const top = window.pageYOffset
          //console.log(document.documentElement.scrollTop)
          if (top > 60) {
              let opacity = top / 140
              opacity = opacity > 1 ? 1 : opacity
              this.opacityStyle = {
                  opacity
              }
              this.showAbs = false
          }else {
              this.showAbs = true
          }
      }
  },
  activated () {
      window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
      window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style scoped>
    .header-abs {
        position: absolute;
        left: .2rem;
        top: .2rem;
        width: .8rem;
        height: .8rem;
        border-radius: .4rem;
        background: rgba(0,0,0,.8);
        color: #fff;
        font-size: .4rem;
        text-align: center;
        line-height: .8rem;
    }
    .header-fixed {
        position: fixed;
        z-index: 2;
        top: 0;
        left: 0;
        right: 0;
        height: .86rem;
        line-height: .86rem;
        text-align: center;
        margin-top: 0;
        background-color: #00bcde;
        color: #fff;
        font-size: .32rem;
    }
    .header-fixed-back {
        position: absolute;
        left: 0;
        top: 0;
        font-size: .4rem ;
        color: #fff;
    }
</style>
