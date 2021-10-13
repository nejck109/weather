<template>

  <Search @search-string="fetchWeather"
        :cityNotValid="cityNotValid"
        :searchHisText="searchString"/> 

  <ShowWeather v-if="showWeatherBlock" 
        :returnedData="returnedData"/>  

  <SearchHistory :searchHistoryArray="searchHistoryArray"
        @search-string="fetchWeather" />
  
</template>

<script>
import Search from './components/Search.vue'
import SearchHistory from './components/SearchHistory.vue'
import ShowWeather from './components/ShowWeather.vue'

export default {
  name: 'App',
  components: {
    Search,
    SearchHistory,
    ShowWeather
  },
  data() {
    return {
      searchHistoryArray: [],
      returnedData: [],
      searchString: '',
      cityNotValid: false,
      showWeatherBlock: false
    }
  },
  methods: {
     async fetchWeather(value) {
        
        this.searchString = value.toLowerCase();
         // Fetch data
        const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.searchString}&appid=8d071f92b0322fc48b1601f4f2e567ce`)
            

            // Check if response was valid and set boolean to true if city was valid
            if(!res.ok){
                this.cityNotValid = true;
                this.showWeatherBlock = false;
            }else{
                this.cityNotValid = false;

                if(this.searchHistoryArray.includes(this.searchString)){
                  var ind = this.searchHistoryArray.indexOf(this.searchString);
                  this.searchHistoryArray.splice(ind, 1);
                }
                this.searchHistoryArray.unshift(this.searchString); // Add at the beggining of search history
                if(this.searchHistoryArray.length > 5){
                  this.searchHistoryArray.pop();
                }
                // Get and return data
                const data = await res.json();
                this.returnedData = data;
                this.showWeatherBlock = true;
                console.log(data)
                return data;
              }
     },

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
