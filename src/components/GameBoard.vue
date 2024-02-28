<template>
    <div id="game-board">
      <!-- Display the spaceship, invaders, and bullets -->
      <SpaceShip v-if="gameActive" />
      <SpaceInvader v-for="invader in invaders" :key="invader.id" />
      <ShipBullet v-for="bullet in bullets" :key="bullet.id" />
  
      <!-- Game start and game over messages -->
      <div v-if="!gameActive && gameInitialized" class="game-over">
        Game Over. Press Space to Restart!
      </div>
      <div v-if="!gameInitialized" class="game-start">
        Press Space to Start!
      </div>
    </div>
  </template>
  
  <script>
  import SpaceShip from './SpaceShip.vue';
  import SpaceInvader from './SpaceInvader.vue';
  import ShipBullet from './ShipBullet.vue';
  
  export default {
    components: {
      SpaceShip,
      SpaceInvader,
      ShipBullet,
    },
    data() {
      return {
        gameActive: false,
        gameInitialized: false,
        invaders: [], // This will hold invader objects
        bullets: [], // This will hold bullet objects
      };
    },
    methods: {
      startGame() {
        // Initialize or reset the game state
        this.gameActive = true;
        this.gameInitialized = true;
        // Setup invaders, reset player position, etc.
      },
      endGame() {
        // Handle game over logic
        this.gameActive = false;
        // Maybe display score or reset certain states
      },
      gameLoop() {
        // Main game loop to update game state and render
        if (this.gameActive) {
          requestAnimationFrame(this.gameLoop);
          // Update positions, check for collisions, etc.
        }
      },
    },
    mounted() {
      // Listen for spacebar press to start/restart game
      window.addEventListener('keydown', (event) => {
        if (event.code === 'Space' && !this.gameActive) {
          this.startGame();
          this.gameLoop();
        }
      });
    },
  };
  </script>
  
  <style scoped>
  #game-board {
    width: 100%;
    height: 100vh;
    background-color: black;
    position: relative;
    overflow: hidden;
  }
  
  .game-over, .game-start {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 24px;
  }
  </style>
  