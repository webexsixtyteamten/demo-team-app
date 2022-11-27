<template>
  <h1>Home</h1>
  <div class="app-content">
    <div class="app-url"><a href="http://localhost:8080/quiz">クイズ</a></div>
    <div class="app-url">
      <a href="http://localhost:8080/palette">パレット</a>
    </div>
    <div class="app-url"><a href="http://localhost:8080/memo">メモ</a></div>
  </div>
</template>
<style scoped>
.app-content {
  display: flex;
  text-align: center;
}
.app-url {
  min-width: 100px;
  font-size: large;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-weight: bold;
}
</style>
