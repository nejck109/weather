<template>
    <form @submit.prevent="onSubmit">
  <input type="text" v-model="searchString">
    <input type="submit">
    <div v-if="cityNotValid">Napacno mesto</div>
     </form>
</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
           searchString: '',
           weatherDataJSON: [],
           searchHistoryArray: [],
           cityNotValid: false 
        }
    },
    methods:{
        async onSubmit(e){

            e.preventDefault();

            // Fetch data
            this.weatherDataJSON = await this.fetchWeather();

            // Add to search History only if response (city) was valid
            if(!this.cityNotValid){

                this.searchHistoryArray.unshift(this.searchString); // Add at the beggining of search history
                this.$emit('search-history', this.searchHistoryArray); // Pass array to parent
                this.$emit('search-data', this.weatherDataJSON); // Pass array to parent
            }
            
            this.searchString = ''; // Delete previous search
            
        },
        async fetchWeather() {
            const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.searchString}&appid=8d071f92b0322fc48b1601f4f2e567ce`)
            
            // Check if response was valid and set boolean to true if city was valid
            if(!res.ok){
                this.cityNotValid = true;
            }else{
                this.cityNotValid = false;
                const data = await res.json()
                         
                return data
            }
    },
    }
}
</script>

<style>

</style>