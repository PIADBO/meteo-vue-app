<template>
    <div> 
        <Meteo v-bind:forecast="forecast"/> 
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Meteo from './Meteo.vue'
import axios from 'axios';


@Component({
  components: {
      Meteo
  },
  props: {latitude: Number,
  longitude : Number}
  
})
export default class Position extends Vue {
  //data
    forecast : object = {};
    isLoading : boolean = true;
    errorcatch : any;
  
  //methods
    getDataWeather() {
        let urlOrigin = 'https://api.openweathermap.org/data/2.5/weather?lat=latitude&lon=longitude&lang=fr&units=metric&appid=acc5f94425cad6ee5536ffe1f44eee56'
        let url = urlOrigin.replace('latitude', this.$props.latitude.toString()).replace('longitude', this.$props.longitude.toString())
        if (this.$props.lat === 0) {return null}
        axios.get(url)
        .then(response => {this.forecast = response.data; this.isLoading = false})
        .catch(error => {this.errorcatch = error})
    }

  //lifecicle
  mounted() {
    this.getDataWeather();
  }
  
  //lifecicle
 
 
}
</script>

<style>


</style>