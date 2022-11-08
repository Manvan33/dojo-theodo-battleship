<script>
import PlayBoard from "./PlayBoard.vue";
import { generateRandomAssets } from "../services/board-helper";

export default {
  data() {
    return {
      playerAssets: {
        boardCells: {},
        boats: {}
      },
      gameStarted: false
    };
  },
  methods: {
    setAssets(object) {
      const tmp = generateRandomAssets();
      object.boardCells = tmp.boardCells;
      object.boats = tmp.boats;
    },
    startGame() {
      this.gameStarted = true;
      this.setAssets(this.playerAssets);
      console.log(this.playerAssets);
    }
  },
  name: "BattleBoard",
  components: { PlayBoard }
};
</script>

<template>
  <PlayBoard
    title="Player"
    :rowsCount="10"
    :columnsCount="10"
    :boardCells="this.playerAssets.boardCells"
  ></PlayBoard>
  <button @click="startGame">Start game !</button>
  <div class="battle-board">
    <div class="title">BattleShip</div>
  </div>
</template>

<style lang="scss" scoped>
.title {
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 30px;
}
.battle-board {
  padding: 30px;
}
</style>
