<template>
    <div class="container">
    <h2>{{returnedData.name}}</h2>
        <div class="flex-container">
            
            <div>
                <p class="bolded">Temperature</p>
                <p>{{this.KtoCelsius(returnedData.main.temp)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">Feels like</p>
                <p>{{this.KtoCelsius(returnedData.main.feels_like)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">Low Temp</p>
                <p>{{this.KtoCelsius(returnedData.main.temp_min)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">High Temp</p>
                <p>{{this.KtoCelsius(returnedData.main.temp_max)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">Humidity</p>
                <p>{{returnedData.main.humidity}}</p>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    name: 'ShowWeather',
    props: ['returnedData'], // Get JSON data from parent
    methods: {
        KtoCelsius(temp){ // Celsius for each temperature in ShwoWeather component
            let strTemp = JSON.stringify(temp);
            strTemp = strTemp - 273.15; // Formula for getting celsius from K 
            return  Math.floor(strTemp); // Get just the whole number
        }
    },  
}
</script>

<style scoped>

 h2{
     color: #FF6720;
     text-transform: uppercase;
 }

 .container {
    width: 60vw;
    margin: 2rem auto;
    padding: 5vh 5vh;
    border-radius: 25px;
    border: 4px solid #593C15;
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
}

@media only screen and (max-width: 980px) {
    .flex-container {
     display: flex;
     flex-direction: column;
     align-items: center;
     justify-content: center;
 }
}
</style>