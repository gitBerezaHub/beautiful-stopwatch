<script lang="ts" setup>
import { ref } from "vue";

let startTime: number;
let stopwatchInterval: number | null;
let elapsedPausedTime = 0;
const displayTime = ref("00:00:00");
const stopwatchState = ref("off"); // 'off', 'on', 'paused'

function startStopwatch() {
  if (!stopwatchInterval) {
    stopwatchState.value = "on";
    startTime = new Date().getTime() - elapsedPausedTime;
    stopwatchInterval = setInterval(updateStopwatch, 1000);
  }
}

function stopStopwatch() {
  stopwatchState.value = "paused";
  if (stopwatchInterval) {
    clearInterval(stopwatchInterval);
  }
  elapsedPausedTime = new Date().getTime() - startTime;
  stopwatchInterval = null;
}

function resetStopwatch() {
  stopStopwatch();
  stopwatchState.value = "off";
  elapsedPausedTime = 0;
  displayTime.value = "00:00:00";
}

function updateStopwatch() {
  let currentTime = new Date().getTime();
  let elapsedTime = currentTime - startTime;
  let seconds = Math.floor(elapsedTime / 1000) % 60;
  let minutes = Math.floor(elapsedTime / 1000 / 60) % 60;
  let hours = Math.floor(elapsedTime / 1000 / 60 / 60);
  displayTime.value = pad(hours) + ":" + pad(minutes) + ":" + pad(seconds);
}

function pad(num: number) {
  return (num < 10 ? "0" : "") + num;
}
</script>

<template>
  <div class="wrapper">
    <div class="stopwatch-part">
      <div class="time">{{ displayTime }}</div>
      <div class="button-menu">
        <button
          class="left-button"
          @click="resetStopwatch"
          v-if="stopwatchState == 'paused'"
        >
          Reset
        </button>
        <button class="left-button" v-else>Interval</button>
        <button
          class="right-button"
          @click="startStopwatch"
          v-if="stopwatchState == 'off'"
        >
          Start
        </button>
        <button
          class="right-button"
          @click="stopStopwatch"
          v-if="stopwatchState == 'on'"
        >
          Pause
        </button>
        <button
          class="right-button"
          @click="startStopwatch"
          v-if="stopwatchState == 'paused'"
        >
          Continue
        </button>
      </div>
    </div>
    <div class="interval-part"></div>
  </div>
</template>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: row;
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/forest.jpg");
  background-repeat: no-repeat;
  background-size: cover;
}

.stopwatch-part,
.interval-part {
  width: 50%;
  height: 100%;
}

.stopwatch-part {
  font-size: 6vw;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
}

.time {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 70%;
  height: 20%;
  background-color: #30444e;
  border-radius: 40px;
}

.button-menu {
  height: 8%;
  width: 70%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.left-button,
.right-button {
  font-size: 28%;
  background-color: #30444e;
  border: none;
  border-radius: 20px;
  color: #fff;
  width: 30%;
  cursor: pointer;
}

.right-button {
  background-color: #3dd598;
}
</style>
