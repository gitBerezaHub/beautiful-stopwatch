<script setup lang="ts">
import BackgroundSelector from "@/components/BackgroundSelector.vue";
</script>

<template>
  <div class="greetings-wrapper">
    <h1 class="greetings">
      Welcome to <br />
      Beautiful Stopwatch
    </h1>
    <p class="choice-text">Choose your style</p>
  </div>
  <background-selector />
</template>

<style scoped lang="scss">
.greetings-wrapper {
  padding-top: 40px;
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
}

.greetings {
  font-size: 36px;
  margin-bottom: 20px;
  text-align: center;
}
.choice-text {
  font-size: 28px;
  margin-bottom: 20px;
}
</style>
