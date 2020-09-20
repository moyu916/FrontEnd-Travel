<template>
    <div class="list" ref="wrapper">
        <div>
          <div class="area">
            <div class="title border-topbottom">您的位置</div>
            <div class="button-list">
                <div class="button-wrapper">
                    <div class="button">{{this.$store.state.city}}</div>
                </div>
            </div>
          </div>
          <div class="area">
            <div class="title border-topbottom">热门城市</div>
            <div class="button-list">
                <div class="button-wrapper" 
                     v-for="item of hot" 
                     :key="item.id" 
                     @click="handleCityClick(item.name)">
                    <div class="button">{{item.name}}</div>
                </div>
            </div>
          </div>
         <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
            <div class="title border-topbottom">{{key}}</div>
            <div class="item-list">
                <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
            </div>
         </div>
      </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
    name: 'CityList',
    props: {
        hot: Array,
        cities: Object,
        letter: String
    },
    methods: {
        handleCityClick (city) {
            //alert(city)
            this.$store.dispatch('changeCity', city)
            this.$router.push('/')
        }
    },
    watch: {
        letter () {
            if (this.letter) {
                this.scroll.scrollToElement(this.$refs[this.letter][0])
                //console.log(this.letter)
            }
            //console.log(this.letter)
        }
    },
        mounted () {
        this.scroll = new BScroll(this.$refs.wrapper,{
            click: true
        }) 
    }
}
</script>

<style scoped>
    .list {
        position: absolute;
        top: 1.58rem;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: hidden;
    }
    .border-topbottom::before {
        border-color: #ccc;
    }
    .border-topbottom::after {
        border-color: #ccc;
    }
    .title {
        line-height: .44rem;
        background-color: #eee;
        padding-left: .2rem;
        color: #666;
        font-size: .26rem;
    }
    .button-list {
        overflow: hidden;
        padding: .1rem;
        padding: .1rem .6rem .1rem .1rem;
    }
    .button-wrapper {
        float: left;
        width: 33.33%;
    }
    .button {
        margin: .1rem;
        line-height: .4rem;
        text-align: center;
        border: .02rem solid #ccc;
        border-radius: .06rem;
    }
    .item {
        line-height: .76rem;
        color: #666;
        padding-left: .2rem;
    }

</style>