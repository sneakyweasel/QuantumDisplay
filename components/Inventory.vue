<template>
  <b-col id="inventory" class="text-white">
    <h2 class="text-center">
      Inventory
    </h2>
    <div>
      <div role="tablist">
        <b-card no-body class="mb-1 bg-dark">
          <b-card-header header-tag="header" class="p-1" role="tab">
            <b-button block href="#" v-b-toggle.accordion-1 variant="info">Reflectors</b-button>
          </b-card-header>
          <b-collapse id="accordion-1" visible accordion="my-accordion" role="tabpanel">
            <b-card-body>
              <b-img src="~assets/tiles/beamsplitter_64.png" fluid alt="beam" rounded="circle" width="32px" />
              <b-img src="~assets/tiles/mirror_64.png" fluid alt="mirror" rounded="circle" width="32px" />
            </b-card-body>
          </b-collapse>
        </b-card>
        <b-card no-body class="mb-1 bg-dark">
          <b-card-header header-tag="header" class="p-1" role="tab">
            <b-button block href="#" v-b-toggle.accordion-2 variant="info">Emitters</b-button>
          </b-card-header>
          <b-collapse id="accordion-2" visible accordion="my-accordion" role="tabpanel">
            <b-card-body>
              <b-img src="~assets/tiles/laser_64.png" fluid alt="laser" rounded="circle" width="32px" />
              <b-img src="~assets/tiles/photon_64.png" fluid alt="photon" rounded="circle" width="32px" />
            </b-card-body>
          </b-collapse>
        </b-card>
        <b-card no-body class="mb-1 bg-dark">
          <b-card-header header-tag="header" class="p-1" role="tab">
            <b-button block href="#" v-b-toggle.accordion-3 variant="info">Detectors</b-button>
          </b-card-header>
          <b-collapse id="accordion-3" visible accordion="my-accordion" role="tabpanel">
            <b-card-body>
              <b-img src="~assets/tiles/detector_64.png" fluid alt="detector" rounded="circle" width="32px" />
            </b-card-body>
          </b-collapse>
        </b-card>
      </div>
    </div>
  </b-col>
</template>

<script>
export default {

}
</script>

<style>
  #inventory {
    background-image: linear-gradient(-90deg, purple, #16161d);
  }

</style>
