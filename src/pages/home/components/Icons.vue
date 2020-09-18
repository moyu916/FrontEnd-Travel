<template>
    <swiper>
        <swiper-slide v-for="(page,index) of pages" :key="index">
            <div class="icons">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img :src="item.imgUrl" alt="">
                    </div>
                    <p>{{item.desc}}</p>
                </div>
            </div>
        </swiper-slide>
    </swiper>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    icons: Array
  },
  computed: {
    pages () {
        const pages = []
        this.icons.forEach((item,index)=>{
            const page = Math.floor(index/8)
            if(!pages[page]){
                pages[page] = []
            }
            pages[page].push(item)
        })
        return pages
      }
  }
}
</script>

<style scoped>
    .icons {
        overflow: hidden;
        width: 100%;
        height: 0;
        padding-bottom: 50%;
    }
    .icon {
        position: relative;
        overflow: hidden;
        float: left;
        width: 25%;
        padding-bottom: 25%;
        height: 0;
    }
    .icon-img {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: .44rem;
        box-sizing: border-box;
        padding: .1rem;
    }
    .icon-img img{
        height: 100%;
        display: block;
        margin: 0 auto;
    }
    .icon p {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        color: #333;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        text-align: center;
    }

</style>
