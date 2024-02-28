<template>
  <div id="app">
    <header>
      <h1>Space Invaders Vue</h1>
    </header>
    <main>
      <GameBoard />
    </main>
  </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue';

export default {
  name: 'App',
  components: {
    GameBoard,
  },
};
</script>

<style>
#app {
  text-align: center;
}

header {
  background-color: #000;
  color: #fff;
  padding: 20px 0;
  font-size: 24px;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90vh;
}
</style>
