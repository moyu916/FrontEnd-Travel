<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont icon-arrow-left">&#xe743;</span>
        </div>
        <div class="header-mid">
            <span class="iconfont icon-search">&#xe6a2;</span>
            <input type="text" value="输入城市/景点/游玩主题">
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{this.$store.state.city}}
                <span class="iconfont icon-list">&#xe6a4;</span>
            </div>
        </router-link>
    </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>

<style scoped>
    .header {
        display: flex;
        width: 100%;
        height: .86rem;
        background-color: #00bcde;
        position: fixed;
        top: 0;
        color: #fff;
        z-index: 2;
    }
    .header-left {
        float: left;
        width: .6rem;
    }
    .header-right {
        box-sizing: border-box;
        float: right;
        min-width: 1.24rem;
        line-height: .86rem;
        padding-right: .5rem;
        color: #fff;
    }
    .icon-arrow-left {
       text-align: center;
       line-height: .86rem;
       font-size: .5rem;
    }
    .icon-list {
        position: absolute;
        right: 0;
        line-height: .86rem;
        font-size:.6rem;
    }
    .icon-search{
        position: absolute;
        left: .18rem;
        top:.24rem;
        color: #ccc;
        font-size: .38rem;
    }
    .header-mid {
        box-sizing: border-box;
        padding: .1rem .1rem;
        flex: 1;
        position: relative;
    }
    .header-mid input {
        display: block;
        box-sizing: border-box;
        padding-left: .5rem;
        height: 100%;
        width: 100%;
        color:#ccc;
        border-radius:.06rem;
    }

</style>
