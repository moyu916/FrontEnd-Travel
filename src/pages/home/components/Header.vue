<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont icon-arrow-left">&#xe743;</span>
        </div>
        <div class="header-mid">
            <span class="iconfont icon-search">&#xe6a2;</span>
            <input type="text" value="输入城市/景点/游玩主题">
        </div>
        <div class="header-right">
            {{this.city}}
            <span class="iconfont icon-list">&#xe6a4;</span>
        </div>
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
    }
    .header-left {
        float: left;
        width: .6rem;

    }
    .header-right {
        float: right;
        width: 1.24rem;
        line-height: .86rem;
        text-align: left;
        padding-left: .05rem;
    }
    .iconfont {
        font-size: .5rem;
    }
    .icon-arrow-left {
       text-align: center;
       line-height: .86rem;
    }
    .icon-list {
        position: absolute;
        line-height: .86rem;
        font-size:.6rem;
    }
    .icon-search{
        position: absolute;
        left: .28rem;
        top:.16rem;
        color: #ccc;
    }
    .header-mid {
        flex: 1;
        position: relative;
    }
    .header-mid input {
        height: calc(100% - 0.2rem);
        width: calc(100% - .6rem);
        color:#ccc;
        border-radius:.06rem;
        margin-top: .1rem;
        padding-left:.6rem;
    }

</style>
