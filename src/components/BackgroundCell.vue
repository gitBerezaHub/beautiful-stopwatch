<script setup lang="ts"></script>

<template>
  <div class="cell">
    <img class="cell-image" src="@/assets/forest.jpg" alt="" />
    <div class="cell-data">
      <div class="name-and-description">
        <h1 class="cell-name">Cell Name</h1>
        <p class="cell-description">Cell description</p>
      </div>
      <div class="likes">
        <img src="@/assets/like.svg" alt="" width="24" />
        <p>42 likes</p>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.cell {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 270px;
  height: 210px;
  background-color: #30444e;
  border-radius: 25px;
  padding: 25px;
}

.cell-image {
  width: 270px;
  height: 160px;
  border-radius: 12px;
}

.cell-data {
  padding-top: 16px;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.name-and-description {
  width: 70%;
}

.likes {
  width: 30%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
</style>
