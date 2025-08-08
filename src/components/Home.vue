<template>
   <div class="text-center">
      <p>Let's play the game</p>
      <h2 class="text-primary pb-3">Current Score: {{ gameStore.getScore }}</h2>
      <span class="text-primary" pb-3
         >Max Score: {{ gameStore.maxHealth }}</span
      >
      <br />
      <div class="row">
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
   </div>
</template>

<script setup>
import { useGameStore } from "../store/gameStore.js";

const gameStore = useGameStore();

function increment() {
   gameStore.score += gameStore.getNextAttack;
}

function decrement() {
   gameStore.score -= gameStore.getNextDefense;
}

function random() {
   Math.random() > 0.5 ? increment() : decrement();
}
</script>
