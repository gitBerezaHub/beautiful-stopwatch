<script setup lang="ts"></script>

<template>
  <router-view />
</template>

<style lang="scss">
@import "styles/reset";

@font-face {
  font-family: SFPRODISPLAYREGULAR;
  src: url("styles/sf-pro-display-font/SFPRODISPLAYREGULAR.OTF");
  font-weight: bold;
}

#app {
  font-family: SFPRODISPLAYREGULAR;
  width: 100vw;
  height: 100%;
  color: #fff;
  background-color: #22343c;
}
</style>
