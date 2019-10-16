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
            :key="indexX * width + indexY"
            :x="indexX"
            :y="indexY"
            :frozen="grid[indexX][indexY].frozen"
            :element="grid[indexX][indexY].element"
            :rotation="grid[indexX][indexY].rotation"
            :photon="grid[indexX][indexY].photon"
          />
        </div>
      </div>
      <controls />
    </div>
  </b-col>
</template>

<script>
import * as qw from 'quantumweasel'
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
      width: 10,
      height: 10,
      grid: [],
      currentFrame: 0,
      isMouseDown: false,
      cells: [
        { x: 1, y: 4, element: 'laser', frozen: false, rotation: 180 },
        { x: 4, y: 4, element: 'beamsplitter', frozen: false, rotation: 180 },
        { x: 7, y: 4, element: 'detector', frozen: true, rotation: 180 },
        { x: 4, y: 7, element: 'detector', frozen: true, rotation: 270 }
      ],
      photons: [
        { x: 2, y: 3, are: '1', width: '64', height: '64', vertical: 'true' },
        { x: 2, y: 4, are: '1', width: '64', height: '64', vertical: 'false' }
      ]
    }
  },
  computed: {
  },
  created () {
    // Create array of cells with empty elements
    for (let x = 0; x < this.width; x++) {
      this.grid[x] = []
      for (let y = 0; y < this.height; y++) {
        const obj = { }
        // Found in obj
        const cell = this.isCellDefined(x, y)
        const photon = this.isPhotonDefined(x, y)
        // Extend object properties
        if (this.isCellDefined(x, y)) {
          obj.cell = cell
        } else {
          obj.cell = { element: 'void', frozen: false, rotation: 0 }
        }
        if (this.isPhotonDefined(x, y)) {
          obj.photon = photon
        }
        // Place in grid
        console.log(obj)
        this.grid[x][y] = obj
      }
    }
  },
  methods: {
    doWeaselStuff (x, y) {
      return qw.grid
    },
    getCell (x, y) {
      return this.grid[x][y]
    },
    setCell (x, y, info) {
      this.grid[x][y] = info
    },
    isCellDefined (x, y) {
      const cells = this.cells.filter((cell) => {
        return (x === cell.x && y === cell.y)
      })
      if (cells.length > 0) {
        console.log(cells)
      }
      return cells[0]
    },
    isPhotonDefined (x, y) {
      const photons = this.photons.filter((photon) => {
        return (x === photon.x && y === photon.y)
      })
      if (photons.length > 0) {
        console.log(photons)
      }
      return photons[0]
    },
    compareCoords (x1, y1, x2, y2) {
      return (x1 === x2 && y1 === y2)
    }
    // includedInCells (x, y) {
    //   this.cells.forEach((cell) => {
    //     if (this.compareCoords(x, y, cell.x, cell.y)) {
    //       return true
    //     } else {
    //       return false
    //     }
    //   })
    // }
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
