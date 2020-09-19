<template>
    <div class="header">城市选择
        <router-link to="/">
            <span class="iconfont header-back">&#xe743;</span>
        </router-link>
    </div>
</template>

<script>
export default {
    name: 'CityHeader',

}
</script>

<style scoped>
    .header {
        position: relative;
        overflow: hidden;
        height: .86rem;
        line-height: .86rem;
        text-align: center;
        margin-top: 0;
        background-color: #00bcde;
        color: #fff;
        font-size: .32rem;
    }
    .header-back {
        position: absolute;
        left: 0;
        top: 0;
        font-size: .4rem ;
        color: #fff;
    }
</style>