<template>
  <b-col cols="8">
    <h1 class="text-center text-white">
      {{ title }}
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
          <cell
            v-for="(row, indexY) in height"
            :key="indexY"
            :x="indexX"
            :y="indexY"
            :frozen="getCell(indexX, indexY).frozen"
            :element="getCell(indexX, indexY).element"
            :rotation="getCell(indexX, indexY).rotation"
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
    'cell': Cell,
    'controls': Controls
  },
  data () {
    return {
      title: 'I - Yt+ is so friendly',
      width: 14,
      height: 10,
      gridList: [],
      particles: [],
      currentFrame: 0,
      isMouseDown: false,
      jsonCells: [
        { x: 3, y: 1, element: 'laser', frozen: false, rotation: 90 },
        { x: 2, y: 1, element: 'mirror', frozen: false, rotation: 0 },
        { x: 3, y: 1, element: 'beamsplitter', frozen: false, rotation: 180 },
        { x: 4, y: 1, element: 'detector', frozen: true, rotation: 90 },
        { x: 5, y: 1, element: 'detector', frozen: false, rotation: 0 }
      ]
    }
  },
  computed: {
  },
  created () {
    // Create array of cells with empty elements
    for (let i = 0; i < this.width; i++) {
      this.gridList[i] = []
      for (let j = 0; j < this.height; j++) {
        // Loop through data cells
        this.jsonCells.forEach((cell) => {
          if (i === cell.y && j === cell.x) {
            this.gridList[cell.x][cell.y] = { element: cell.element, frozen: cell.frozen, rotation: cell.rotation }
          } else {
            this.gridList[cell.x][cell.y] = { element: 'void', frozen: false, rotation: 0 }
          }
        })
      }
    }
  },
  methods: {
    getCell (x, y) {
      return this.gridList[x][y]
    },
    setCell (x, y, info) {
      this.gridList[x][y] = info
    },
    compareCoords (x1, y1, x2, y2) {
      return (x1 === x2 && y1 === y2)
    },
    includedInCells (x, y) {
      this.cells.forEach((cell) => {
        if (this.compareCoords(x, y, cell.x, cell.y)) {
          return true
        } else {
          return false
        }
      })
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
