<template>
  <div class="playboard">
    <div class="title">{{ title }}</div>
    <div class="grid-container">
      <div class="line" v-for="line in rowsCount" :key="line">
        <div
          class="cell"
          v-for="col in columnsCount"
          :key="col"
          :class="getCellStatus(line, col)"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PlayBoard",
  props: {
    title: String,
    columnsCount: Number,
    rowsCount: Number,
    boardCells: {
      type: Object,
      default: null
    }
  },
  methods: {
    getCellStatus(row, column) {
      try {
        const alpha = "ABCDEFGHIJ";
        return this.boardCells[alpha[row] + column.toString()].status;
      } catch (e) {
        return "";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.playboard {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.line {
  margin: 0px;
  width: fit-content;
  display: flex;
  border-top: 1px solid black;
  border-bottom: 1px solid black;
  & + & {
    border-top: none;
  }
}
.cell {
  border-left: 1px solid black;
  border-right: 1px solid black;
  & + & {
    border-left: none;
  }
  height: 3vw;
  width: 3vw;
}
.ship {
  background-color: black;
}
.ship.hidden {
  background-color: unset;
}
.missed {
  background-color: aqua;
}
.hit {
  background-color: yellow;
}
.sunk {
  background-color: red;
}
</style>
