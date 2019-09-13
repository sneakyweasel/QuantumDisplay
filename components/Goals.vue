<template>
  <b-col id="goals">
    <h2 class="text-center text-white">
      Goals
    </h2>
    <b-list-group id="goal_list" class="bg-dark">
      <b-list-group-item class="bg-dark text-white">
        <small>Detector 1</small>
        <b-progress :value="50" variant="danger" :striped="striped" />
        <small>Detector 2</small>
        <b-progress :value="40" variant="danger" :striped="striped" />
        <small>Detector 3</small>
        <b-progress :value="70" variant="danger" :striped="striped" />
      </b-list-group-item>
    </b-list-group>
    <b-card class="bg-dark text-white">
      <strong>
        Objectives
      </strong>
      <small>Activate any detector to 100%</small>
    </b-card>
  </b-col>
</template>

<script>
export default {

}
</script>

<style>
  #goals {
    background-image: linear-gradient(-90deg, #16161d, purple);
  }
</style>
