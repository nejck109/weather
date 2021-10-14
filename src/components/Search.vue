<template>
    <form @submit.prevent="onSubmit" >
  <input type="text" v-model="searchHisText" :placeholder="this.searchHisText">
    <input type="submit" :disabled="searchHisText.length === 0" value="SEARCH">
    <div class="error-message" v-if="cityNotValid">{{errorText}}</div>
     </form>
</template>

<script>
export default {
    name: 'Search',
    props: ['cityNotValid', 'searchHisText'], // Initial value in input field is set by searchHisText
          // CityNotValid is for displaying error message when city was not found in response
    
    data() {
        return {
           errorText: 'City with that name was not found.' // Error field text
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault();
            this.$emit('search-string', this.searchHisText); // Pass search string to parent
        },
       
    }
}
</script>

<style scoped>
.error-message {
  color: #cc0033;
  font-family: Helvetica, Arial, sans-serif;
  font-size: 13px;
  font-weight: bold;
  line-height: 20px;
  text-shadow: 1px 1px rgba(250,250,250,.3);
  padding: 10px 30px;
}
input[type=text] {
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  padding: 10px 20px 10px 20px;
  margin-right: 10px;
}

input[type=submit] {
    border-radius: 15px;
    font-weight: bold;
    text-transform: uppercase;
    border: 2px solid #593C15;
    color: #FF6720;
    padding: 12px 24px;
    text-decoration: none;
    margin: 4px 2px;
    cursor: pointer;
}
</style>