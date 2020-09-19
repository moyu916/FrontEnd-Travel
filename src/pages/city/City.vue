<template>
    <div>
        <CityHeader></CityHeader>
        <CitySearch></CitySearch>
        <CityList 
            :cities="cities" 
            :hot="hotCities"
            :letter="letter"
        ></CityList>
        <CityAlphabet 
            :cities="cities"
            @change="handleLetterChange"
        ></CityAlphabet>
    </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
export default {
    name: 'City',
    components: {
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
    },
    data () {
        return {
          cities: {},
          hotCities: [],
          letter: ''
        }
    },
    methods: {
        getCityInfo () {
          axios.get('/api/city.json')
            .then(this.getCityInfoSucc)
        },
        getCityInfoSucc (res) {
            //console.log(res)
            res = res.data
            if(res.ret && res.data) {
              this.cities = res.data.cities
              this.hotCities = res.data.hotCities
            }

        },
        handleLetterChange (letter) {
            this.letter = letter
            //console.log(this.letter)
        }       
    },
    mounted () {
        this.getCityInfo()
    }  
}
</script>

<style scoped>

</style>
