<template>
  <div class="meteo">
    
      <h3>{{ forecast.name }}</h3>

        <p v-if="forecast.weather[0].description.match('pluie') !== null"><img src="../assets/weather/rain.svg" alt="icon" class="my-4" height="150px" width="150px"></p>

        <p v-if="forecast.weather[0].description.match('ciel') !== null"><img src="../assets/weather/sun.svg" alt="icon" class="my-4" height="150px" width="150px"></p>

        <p v-if="forecast.weather[0].description.match('nuage') !== null || forecast.weather[0].description.match('couvert') !== null"><img src="../assets/weather/cloud.svg" alt="icon" class="my-4" height="150px" width="150px"></p>

        <p v-if="forecast.weather[0].description.match('orage') !== null"><img src="../assets/weather/storm.svg" alt="icon" class="my-4" height="150px" width="150px"></p>

        <p v-if="forecast.weather[0].description.match('neige') !== null"><img src="../assets/weather/snow.svg" alt="icon" class="my-4" height="150px" width="150px"></p>

        <p v-if="forecast.weather[0].description.match('brume') !== null"><img src="../assets/weather/tornado.svg" alt="icon" class="my-4" height="150px" width="150px"></p>
        
       
        <p>{{ forecast.weather[0].description }}</p>
        <p>{{ Math.floor(forecast.main.temp) }} °C</p>
        <p> <img src="../assets/cold.svg" alt="sunrise" height="40px"
    width="40px"> {{ Math.floor(forecast.main.temp_min) }} °C | {{ Math.floor(forecast.main.temp_max) }} °C <img src="../assets/hot.svg" alt="sunrise" height="40px"
    width="40px"> </p>
        <p v-if="sunset == ''"> 0{{ this.sunriseUTC() }} <img src="../assets/sunrise.svg" alt="sunrise" height="40px"
    width="40px">  | <img src="../assets/sunset.svg" alt="sunrise" height="40px"
    width="40px"> {{ this.sunsetUTC() }}</p>
      
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';


@Component({
  components: {
  },
  props: {forecast: Object}
  
})
export default class Meteo extends Vue {
  //data
  sunrise : string = '';
  sunset : string = '';
  
  //computer

  computedUTC(utcStamp : number) {
    var date = new Date(utcStamp*1000);
    // Hours part from the timestamp
    var hours = date.getHours();
    // Minutes part from the timestamp
    var minutes = date.getMinutes();
    // Seconds part from the timestamp
    var seconds = "0" + date.getSeconds();
    let hourComputed : string;

    return hourComputed = ((hours) + 'h' + minutes).toString();
  }

  sunriseUTC() {
    //if (!this.$props.forecast) {return null}
    return this.computedUTC(this.$props.forecast.sys.sunrise);
  }

  sunsetUTC() {
   // if (!this.$props.forecast) {return null}
    return this.computedUTC(this.$props.forecast.sys.sunset);
  }

  //lifecicle
  mounted() {
    this.sunriseUTC();
    this.sunsetUTC();
  }
 
}
</script>
 
<style>
  .meteo {
     text-align: center;
  }
</style>
