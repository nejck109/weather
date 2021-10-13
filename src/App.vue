<template>
  <Search @search-history="getSearchHistory"
          @search-data="getSearchData"/>
  <SearchHistory :searchHistoryArray="searchHistoryArray" />
  <div>{{this.searchData}}</div>
</template>

<script>
import Search from './components/Search.vue'
import SearchHistory from './components/SearchHistory.vue'

export default {
  name: 'App',
  components: {
    Search,
    SearchHistory
  },
  data() {
    return {
      searchHistoryArray: [],
      searchData: []
    }
  },
  methods: {
    getSearchHistory(value){
      this.searchHistoryArray = value;
    },
    getSearchData(value){
      this.searchData = value;
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
