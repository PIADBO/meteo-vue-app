<template>
  <div class="container-fluid">
    <p>Application Meteo</p>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';


@Component({
  components: {},
})
export default class Header extends Vue {
  //data

  //methods

  //lifecicle
}
</script>

<style scoped>
    .container-fluid {
        text-align: left;
        padding : 0;
        background-color : #FFAD69;
    }
    p {
        padding : 5px 5px;
        font-size: 12px;
        background-color : #FFAD69;
    }

</style>