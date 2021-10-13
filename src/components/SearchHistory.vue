<template>
  <div>{{maxFiveHistoryEl}}</div>
</template>

<script>
export default {
    name: 'SearchHistory',
    props: ['searchHistoryArray'],
    computed:{
        maxFiveHistoryEl(){
            if(this.searchHistoryArray.length > 5){
                this.searchHistoryArray.pop();
            }
            return this.searchHistoryArray;
        }
    }

}
</script>

<style>

</style>