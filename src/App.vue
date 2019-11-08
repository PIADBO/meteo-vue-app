<template>
  <div class="container" id="app">
    <Header />
      <div v-if="lat !== 0">
        <Position v-bind:latitude="lat" v-bind:longitude="lng" />
      </div>
    <Footer />
  
      
    
    
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Position from './components/Position.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

@Component({
  components: {
    Position,
    Header,
    Footer
  },
})
export default class App extends Vue {
  //data
  city : string = 'ville';
  forecast : object = {};
  isLoading : boolean = true;
  waiting : string = 'waiting for data';
  lat : number = 0;
  lng : number = 0;

  //methods
   getDataPosition() {
    if (navigator.geolocation){
      navigator.geolocation.getCurrentPosition(
          data => {this.lat = data.coords.latitude;this.lng = data.coords.longitude; console.log(data)},
          error => {console.log(error)}
       )
    }

    console.log("Pas d'accés à la geolocalisation");

  }

  //lifecicle
  beforeMount() {
    this.getDataPosition();
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  margin-top: 10px;
}
#app.container {
  width : 300px;
  border : 2px solid #c5c5c5;
  border-radius: 10px;
  padding : 0;
}
</style>
