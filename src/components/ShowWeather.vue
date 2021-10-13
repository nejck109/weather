<template>
    <div class="container">
    <h2>{{returnedData.name}}</h2>
        <div class="flex-container">
            
            <div>
                <p class="bolded">Temperature</p>
                <p>{{this.FtoCelsius(returnedData.main.temp)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">Feels like</p>
                <p>{{this.FtoCelsius(returnedData.main.feels_like)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">Low Temp</p>
                <p>{{this.FtoCelsius(returnedData.main.temp_min)}}<span>&#8451;</span></p>
            </div>

            <div>
                <p class="bolded">High Temp</p>
                <p>{{this.FtoCelsius(returnedData.main.temp_max)}}<span>&#8451;</span></p>
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
    props: ['returnedData'],
    methods: {
        FtoCelsius(temp){
            let strTemp = JSON.stringify(temp);
            strTemp = strTemp - 273.15;
            return  Math.floor(strTemp);
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