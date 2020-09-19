<template>
    <ul class="alphabet">
        <li class="item" v-for="(item,key) of cities" :key="key"
            @click="handleLetterClick"
            @touchstart="handleTouchStart"
            @touchmove="handleTouchMove"
            @touchend="handleTouchEnd"
            :ref="key">{{key}}</li>        
    </ul>
</template>

<script>
export default {
    name: 'CityAlphabet',
    props: {
        cities: Object
    },
    data () {
        return {
            touchStatus: false
        }
    },
    computed: {
        letters() {
            let letters = []
            for (let i in this.cities) {
                letters.push(i)
            }
            return letters
        }
    },
    methods: {
        handleLetterClick (e) {
            this.$emit('change',e.target.innerText)
            //console.log(e.target.innerText)
        },
        handleTouchStart () {
            this.touchStatus = true
        },
        handleTouchMove (e) {
            if(this.touchStatus) {
                const startY = this.$refs['A'][0].offsetTop
                const touchY = e.touches[0].offsetTop - startY
                const index = Math.floor((touchY - startY) / 20)
                if(index >= 0 && index < this.letters.length) {
                    this.$emit('change',this.letters[index])
                }

                //console.log(startY)
            }
        },
        handleTouchEnd () {
            this.touchStatus = false
        }
    }

}
</script>

<style scoped>
    .alphabet {
        display: flex;
        flex-direction: column;
        justify-content: center;
        position: absolute;
        top: 1.58rem;
        right: 0;
        bottom: 0;
        width: .4rem;
    }
    .item {
        text-align: center;
        line-height: .3rem;
        color: #00bcde;
        font-size: .2rem;
    }
</style>