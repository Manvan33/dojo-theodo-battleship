<script>
import PlayBoard from "./PlayBoard.vue";

export default {
  name: "BattleBoard",
  components: { PlayBoard }
};
</script>

<template>
  <PlayBoard title="Player" :rowsCount="10" :columnsCount="10"></PlayBoard>
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
