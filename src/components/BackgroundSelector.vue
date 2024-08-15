<script setup lang="ts">
import BackgroundCell from "@/components/BackgroundCell.vue";
import router from "@/router";
</script>

<template>
  <div class="cell-grid">
    <div class="background-cell" v-for="index in 9" :key="index">
      <background-cell @click="router.push('/stopwatch')" />
    </div>
  </div>
</template>

<style scoped lang="scss">
.cell-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, 340px);
  grid-auto-rows: 20px;
  grid-gap: 10px;
  justify-content: center;
}

.background-cell {
  display: flex;
  justify-content: center;
  grid-row-end: span 10;
  cursor: pointer;
  position: relative;
  z-index: 0;
}

.background-cell:before {
  content: "";
  background: #286053;
  position: absolute;
  top: -6px;
  background-size: 400%;
  z-index: -1;
  filter: blur(5px);
  width: 100%;
  height: 95%;
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  border-radius: 25px;
}

.background-cell:active:after {
  background: transparent;
}

.background-cell:hover:before {
  opacity: 1;
}

.background-cell:after {
  z-index: -1;
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  border-radius: 10px;
}

@keyframes glowing {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}
</style>
