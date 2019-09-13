
<template>
  <div class="container">
    <b-container fluid class="bv-example-row">
      <b-row>
        <Goals />
        <Grid />
        <Inventory />
      </b-row>
    </b-container>
  </div>
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

<style>
  body {
      background: #16161d !important;
      font: 1rem/1.5 var(--font-family-monospace);
      }
</style>
