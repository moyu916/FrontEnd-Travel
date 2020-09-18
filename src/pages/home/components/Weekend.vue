<template>
    <div class="weekend">
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item" v-for="item of weekend" :key="item.id">
                <div class="img-wrapper">
                    <img :src="item.imgUrl" alt="">
                </div>
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "HomeWeekend",
    props: {
        weekend: Array
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
        height: 0;
        padding-bottom: 50%;
    }
    .img-wrapper {
        height: 2.5rem;
    }
    .img-wrapper img {
        height: 100%;
        width: 100%;
    }
    .item-title {
        margin: .2rem 0;
    }
    .item-desc {
        margin-bottom: .1rem;
        color: #bbb;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }
</style>
