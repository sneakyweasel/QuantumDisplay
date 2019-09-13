<template>
  <b-col cols="8">
    <h1 class="text-center text-white">
      Level 1: Weasel, save the world!
    </h1>
    <div>
      <div
        class="game-grid columns"
        @mousedown="isMouseDown = true"
        @mouseup="isMouseDown = false"
        @mouseleave="isMouseDown = false"
      >
        <div
          v-for="(col, indexX) in width"
          :key="indexX"
          class="game-column"
        >
          <grid-cell
            v-for="(isAlive, indexY) in height"
            :key="indexY"
            :status-obj="isAlive"
            :x-pos="indexX"
            :y-pos="indexY"
          />
        </div>
      </div>
      <controls />
    </div>
  </b-col>
</template>

<script>
import Cell from './Cell'
import Controls from './Controls'
export default {
  components: {
    'grid-cell': Cell,
    'controls': Controls
  },
  data () {
    return {
      width: 14,
      height: 10,
      gridList: [],
      currentFrame: 0,
      isMouseDown: false,
      cells: [
        { x: 1, y: 1, cell: 'laser', frozen: false },
        { x: 2, y: 1, cell: 'mirror', frozen: false },
        { x: 3, y: 1, cell: 'beamsplitter', frozen: false },
        { x: 4, y: 1, cell: 'detector', frozen: false },
        { x: 5, y: 1, cell: 'detector', frozen: false }
      ]
    }
  },
  created () {
    // this.cellCalc()
  },
  methods: {
    cellCalc: () => {
      for (let i = 0; i < this.width; i++) {
        this.gridList[i] = []
        for (let j = 0; j < this.height; j++) {
          if (this.cells.includes([i, j])) {
            this.gridList[i][j] = { isAlive: false }
            this.setCell(i, j, true)
          }
        }
      }
    }
  },
  setCell: (x, y, bool) => {
    if (this.gridList[x][y].isAlive !== bool) {
      this.gridList[x][y].isAlive = bool
    }
  }
}
</script>

<style lang="scss">
.game-grid {
  border-top: 1px solid #1a0707;
  border-left: 1px solid #1a0707;
  display: flex;
  flex: 1;
  justify-content: center;
}
.game-column {
  // flex: 1;
  // display: flex;
  justify-content: center;
  // padding: 0;
  // margin: 0 auto;
  flex-direction: column;
}
  // .grid {
  //   display: grid;
  //   grid-template-columns: repeat(auto-fill, minmax(8rem, 1fr));
  //   grid-auto-rows: 1fr;
  // }

  // .grid::before {
  //   content: '';
  //   width: 0;
  //   padding-bottom: 100%;
  //   grid-row: 1 / 1;
  //   grid-column: 1 / 1;
  // }

  // .grid > *:first-child {
  //   grid-row: 1 / 1;
  //   grid-column: 1 / 1;
  // }

  /* Just to make the grid visible */
  // .grid > * {
  //   background: rgba(0,0,0,0.1);
  //   border: 1px white solid;
  // }
</style>
