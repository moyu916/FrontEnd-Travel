<template>
    <div class="recommend">
        <div class="title">热销推荐</div>
        <ul>
            <router-link 
              tag="li" 
              class="item boeder-bottom" 
              v-for="item of recommend" 
              :key="item.id" 
              :to="'/detail/'+item.id"
            >
                <div class="img-wrapper">
                    <img :src="item.imgUrl" alt="">
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button>查看详情</button>
                </div>
            </router-link>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'HomeRecommend',
    props: {
        recommend: Array
    }
}
</script>

<style scoped>
    .title {
        text-indent: .2rem;
        text-align: left;
        margin-top:.2rem;
        background-color: #eee;
        padding: .15rem 0;
    }
    .item {
        overflow: hidden;
        display: flex;
        height: 1.8rem;
    }
    .item img {
        height: 1.7rem;
        width: 1.7rem;
        padding: .1rem;
    }
    .item-info {
        flex: 1;
        padding: .1rem;
    }
    .item-title {
        margin: .2rem 0;
    }
    .item-desc {
        margin-bottom: .1rem;
        color: #bbb;
    }
    .item-info button {
        color: #fff;
        background-color: #ff9300;
        padding: 0 .2rem;
        border-radius: .06rem;
        font-size: .12rem;
    }
</style>
