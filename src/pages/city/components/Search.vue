<template>
    <div class="search">
        <input type="text" placeholder="输入城市名/拼音">
    </div>
</template>

<script>
export default {
    name: 'CitySearch',

}
</script>

<style scoped>
    .search {
        height: .72rem;
        background-color: #00bcde;
        padding: 0 .1rem;
    }
    .search input {
        box-sizing: border-box;
        height: .62rem;
        line-height: .62rem;
        width: 100%;
        text-align: center;
        border-radius: .06rem;
        color: #666;
        padding: 0 .1rem;
    }
</style>