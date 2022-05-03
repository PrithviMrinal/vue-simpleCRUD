<script>
import { anyWinner } from "./game-logic";

export default {
  name: "TicTacToe",
  components: {},
  data() {
    return {
      board: ["", "", "", "", "", "", "", "", ""],
      turn: 'X',
    };
  },
  methods: {
    toggleTurn: function () {
      if(this.turn==='X'){
        this.turn='0';
      }
      else {
        this.turn = 'X';
      }
    },
    tick: function (index) {
      this.board[index] = this.turn;
      this.toggleTurn();
    },
  },
};
</script>

<template>
  <h1 class="text-3xl font-bold text-blue-900 mb-10">TicTacToe Game</h1>
<!--  <div class="max-w-lg content-center m-auto">
    <div class="grid grid-cols-3 gap-2 content-start w-fulltext-center p-4">
      <div
        v-for="(val, index) in board"
        :key="index"
        class="bg-slate-100 drop-shadow-md cursor-pointer align-middle p-8 h-32 rounded-md text-slate-100 font-bold"
        :class="{
          'bg-blue-500': val === 'X',
          'bg-red-500': val === 'O',
          'hover:drop-shadow-lg': val === '',
          'cursor-not-allowed': val !== '',
        }"
      >
        {{ index }}
      </div>
    </div>
  </div>-->
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
