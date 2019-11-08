<template>
  <div class="container-fluid">
    <p><em>by pierreaconcept.com</em></p>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';


@Component({
  components: {},
})
export default class Footer extends Vue {
  //data

  //methods

  //lifecicle
}
</script>

<style  scoped>
  .container-fluid {
        text-align: center;
        padding : 0;
        background-color : #FFAD69;
    }
    p {
        padding : 5px 5px;
        margin : 0;
        font-size: 12px;
        background-color : #FFAD69;
    }
</style>