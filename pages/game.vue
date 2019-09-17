
<template>
  <client-only>
    <div class="container">
      <b-container fluid class="bv-example-row">
        <b-row>
          <Goals />
          <Grid />
          <Inventory />
        </b-row>
      </b-container>
    </div>
  </client-only>
</template>

<script>
import Grid from '~/components/Grid.vue'
import Goals from '~/components/Goals.vue'
import Inventory from '~/components/Inventory.vue'

export default {
  components: {
    Goals,
    Inventory,
    Grid
  }
}
</script>

<style lang="scss">
  /* @import url('https://fonts.googleapis.com/css?family=Saira+Stencil+One&display=swap'); */
  @import url('https://fonts.googleapis.com/css?family=Karla&display=swap');
  body {
      background: #16161d !important;
      font-family: 'Karla', cursive;
      }
</style>
