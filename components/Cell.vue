<template>
  <div
    v-if="cell"
    :class="[
      'cell',
      cell.element,
      cell.frozen ? 'frozen' : 'unfrozen',
      rotationClass
    ]"
    @click="rotate"
  >
    <p class="coordinates">
      {{ coordinates }}
    </p>
    <div v-if="cell && cell.photon">
      <photon :width="64" :height="64" :margin="0" :are="cell.photon.are" />
    </div>
  </div>
</template>

<script>
import * as qt from 'quantum-tensors'
import Photon from './Photon.vue'

// export interface PhotonInterface {
//   are: number,
//   aim: number,
//   bre: number,
//   bim: number
// }

export default {
  components: {
    'photon': Photon
  },

  props: {
    x: {
      default: -1,
      type: Number
    },
    y: {
      default: -1,
      type: Number
    },
    element: {
      default: 'void',
      type: String
    },
    frozen: {
      default: false,
      type: Boolean
    },
    rotation: {
      default: 0,
      type: Number
    }
  },
  data () {
    return {
      cell: {},
      photon: {}
    }
  },
  computed: {
    coordinates () {
      return `[${this.x}, ${this.y}]`
    },
    rotationClass () {
      return 'rotation_' + this.$props.rotation
    }
  },
  methods: {
    rotate () {
      this.rotation = (this.rotation + 90) % 360
    },
    quantumStuff (a, b) {
      const complex = qt.Cx(a, b)
      console.log(complex.toString())
    }
  }
}
</script>

<style lang="scss">
  .frozen {
    background-color: rgb(0, 104, 189) !important;
  }
  .laser {
     background: url(~assets/tiles/laser_64.png);
     background-repeat: no-repeat;
     background-size: contain;
  }
  .detector {
     background: url(~assets/tiles/detector_64.png);
     background-repeat: no-repeat;
     background-size: contain;
  }
  .mirror {
     background: url(~assets/tiles/mirror_64.png);
     background-repeat: no-repeat;
     background-size: contain;
  }
  .beamsplitter {
     background: url(~assets/tiles/beamsplitter_64.png);
     background-repeat: no-repeat;
     background-size: contain;
  }

  .rotation_0 {
     transform: rotate(0deg);
  }
  .rotation_90 {
     transform: rotate(90deg);
  }
  .rotation_180 {
     transform: rotate(180deg);
  }
  .rotation_270 {
     transform: rotate(-90deg);
  }
  .coordinates {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 12px;
    color: grey;
    text-align: center;
    padding-top: 15px;
  }
  .cell {
    border-right: 1px solid #1a0707;
    border-bottom: 1px solid #1a0707;
    width: 50px;
    height: 50px;
    background-color: rgb(33, 13, 71);
    border: 0%;
    &:hover {
      background-color: rgba(75, 25, 109, 1);
    }
  }
</style>
