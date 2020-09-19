<template>
  <div class="wrapper">
    <swiper ref="mySwiper" :options="swiperOptions" v-if="list.length">
      <swiper-slide v-for="item of list" :key="item.key">
          <img class="swiper-img" :src="item.imgUrl" alt="">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>

</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOptions: {
        pagination: {
          el: '.swiper-pagination'
        },
        loop: true
      }
    }
  }
}
</script>

<style scoped>
    .wrapper {
        width: 100%;
        /* overflow: hidden;
        height: 0; //31.25%是相对于父元素的高度，而非自身宽度
        padding-bottom: 31.25% */
        height: 31.25vw;
        margin-top: .86rem;

    }
    .swiper-img {
        width: 100%;
    }

</style>
