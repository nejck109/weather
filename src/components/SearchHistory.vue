<template>
    <h2>{{title}}</h2>
    <div class="flex-container">
  <div class="bolded" @click="this.$emit('search-string', searchString);" v-for="(searchString, index) in searchHistoryArray" :key=index>{{searchString}}</div>
    </div>
</template>

<script>
export default {
    name: 'SearchHistory',
    props: ['searchHistoryArray'],
    data() {
        return{
            title: 'Search History'
        }
    },
    emits: ['searchString', 'search-string']
}
</script>

<style scoped>
h2{
    padding-top: 2rem;
     color: #FF6720;
     text-transform: uppercase;
 }
.flex-container {
     display: flex;
     flex-direction: row;
     align-items: center;
     justify-content: center;
 }
 .flex-container > div {
    text-align: center;
    text-transform: uppercase;
    margin: 1rem;
    padding: 20px;
    font-family:Helvetica Neue, Helvetica, Arial, sans-serif;
    font-size: 16px;
}
.bolded {
    font-weight: bold;
    cursor: pointer;
    border-radius: 15px;
    border: 2px solid #593C15;
}
</style>