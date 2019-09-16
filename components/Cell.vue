<template>
  <div
    @click="rotate()"
    :class="[
      frozen ? 'frozen' : '',
      element,
      {rotation}
    ]"
    class="cell"
  >
    <p class="coordinates">
      {{ this.coordinates }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    x: {
      default: -1,
      type: Number
    },
    y: {
      default: -1,
      type: Number
    },
    rotation: {
      default: 0,
      type: Number
    },
    frozen: {
      default: false,
      type: Number
    }
  },
  data () {
    // return {
    //   x: 0,
    //   y: 0,
    //   element: 'void',
    rotation: 0
    //   frozen: this.frozen
    // }
  },
  computed: {
    coordinates () {
      return `[${this.x}, ${this.y}]`
    },
    classes () {
      return `${this.element}, ${this.isFrozen}, rotate_${this.rotation}`
    }
  },
  methods: {
    rotate: () => {
      this.props.rotation += 90 
    }
  }
}
</script>

<style lang="scss">
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
  .frozen {
    background-color: aquamarine;
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

  .rotate_0, .down {
     transform: rotate(0deg);
  }
  .rotate_90, .up {
     transform: rotate(90deg);
  }
  .rotate_180, .right {
     transform: rotate(180deg);
  }
  .rotate_270, .left {
     transform: rotate(-90deg);
  }
  .coordinates {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 12px;
    color: grey;
    text-align: center;
    padding-top: 15px;
  }
</style>
