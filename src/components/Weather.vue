<script>
import axios from 'axios';

export default {
  data() {
    return {
      weatherData: {}
    };
  },
  mounted() {
    const apiKey = '7b304ef46c450eb141e5c507431d9725';
    const city = 'Paris';
    const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;
    
    axios.get(apiUrl)
      .then(response => {
        this.weatherData = response.data;
        console.log(this.weatherData)
      })
      .catch(error => {
        console.error(error);
      });
  } 
};
</script>

<template>
    <div class="weather">
      <h1>{{ weatherData.name }}</h1>
      <div class="weather-details">
        <p class="temperature">{{ weatherData.main.temp }}°C</p>
        <p class="description">{{ weatherData.weather[0].description }}</p>
      </div>
    </div>
  </template>
  
  <style scoped>
  .weather {
    text-align: center;
  }
  
  .weather h1 {
    font-size: 24px;
    margin-bottom: 10px;
  }
  
  .weather .weather-details {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .weather .temperature {
    font-size: 48px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .weather .description {
    font-size: 16px;
  }
  </style>
  
