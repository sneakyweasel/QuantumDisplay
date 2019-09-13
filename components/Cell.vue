<template>
  <div class="cell" />
</template>

<script>
export default {
  props: {
    xPos: {
      default: -1,
      type: Number
    },
    yPos: {
      default: -1,
      type: Number
    },
    isMouseDown: {
      default: false,
      type: Boolean
    }
  },
  data () {
    return {
      // The status for a single cell.
      // Sadly it is an anti pattern because ES2015 / Vue
      // do have some problems to deal with a 2D-Array (not-reactive).
      // If you have a different idea how to fix this create an issue :)
      isAlive: this.statusObj
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
      background-color: rgba(75, 25, 109, 0.6);
    }
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
</style>
