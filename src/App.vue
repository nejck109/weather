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
      searchHistoryArray: [], // Search History
      returnedData: [], // JSON data
      searchString: '', // Searched string
      cityNotValid: false, // Remember if city was not found
      showWeatherBlock: false // If city was found, show it's weather info
    }
  },
  methods: {

    alreadyInList(){
      if(this.searchHistoryArray.includes(this.searchString)){
          var ind = this.searchHistoryArray.indexOf(this.searchString);  // If it is, remember index
          this.searchHistoryArray.splice(ind, 1); // Delete it
        }
    },
    maxFiveItems(){
       if(this.searchHistoryArray.length > 5){ 
            this.searchHistoryArray.pop(); // If we already have 5 history items, delete the last one.
        }
    },
    async fetchWeather(value) {
        
      this.searchString = value.toLowerCase(); // get search string and transform to lower case - (includes method case sensitive)
        
      // Fetch data
      const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.searchString}&appid=8d071f92b0322fc48b1601f4f2e567ce`)
            

      // Check if response was valid 
      if(!res.ok){

        this.cityNotValid = true; // Set city boolean to true if city was not valid
        this.showWeatherBlock = false; // Do not show weather for invalid response
      }else{
        this.cityNotValid = false;

        // Check if search string is already in history list
        this.alreadyInList();

        this.searchHistoryArray.unshift(this.searchString); // Add at the beggining of search history
                
        this.maxFiveItems();

        const data = await res.json(); // Get data
        this.returnedData = data; // Save data
        this.showWeatherBlock = true; // Show weather for responce
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
