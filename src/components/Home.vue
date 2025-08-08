<template>
   <div class="text-center">
      <p>Let's play the game</p>
      <h2 class="text-primary pb-3">Current Score: {{ gameStore.getScore }}</h2>
      <span class="text-primary" pb-3
         >Max Score: {{ gameStore.maxHealth }}</span
      >
      <br />
      <span v-if="gameStore.getScore >= gameStore.maxHealth" class="text-success pb-3 h3">
         You Won!
      </span>
      <span class="text-danger pb-3 h3" v-if="gameStore.getScore < 0">
         You Lost!
      </span>
      <div
         class="row"
         v-if="gameStore.getScore < gameStore.maxHealth && gameStore.getScore >= 0"
      >
         <div class="col-5 offset-1">
            <button @click="increment" class="form-control btn btn-success p-4">
               Increment
            </button>
         </div>
         <div class="col-5 offset-1">
            <button @click="decrement" class="form-control btn btn-danger p-4">
               Decrement
            </button>
         </div>
         <div class="col-6 offset-3 pt-2">
            <button @click="random" class="form-control btn btn-warning p-4">
               Random
            </button>
         </div>
      </div>
      <div v-else>
         <button
            class="form-control btn btn-primary p-4"
            @click="gameStore.resetScore()"
         >
            Restart Game
         </button>
      </div>
   </div>
</template>

<script setup>
import { useGameStore } from "../store/gameStore.js";

const gameStore = useGameStore();

function increment() {
   gameStore.setNextAttack();
}

function decrement() {
   gameStore.setNextDefense();
}

function random() {
   Math.random() > 0.5 ? increment() : decrement();
}
</script>
