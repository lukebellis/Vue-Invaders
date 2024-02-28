<template>
    <div class="space-invader" :style="invaderStyle">
      <img src="@/assets/SpaceInvader.webp" alt="Space Invader" />
    </div>
  </template>
  
  <script>
  export default {
    props: {
      // Assuming each invader's position is controlled by the parent
      position: {
        type: Object,
        required: true,
      },
    },
    computed: {
      invaderStyle() {
        // Use the position prop to position the invader on the game board
        return {
          left: `${this.position.x}px`,
          top: `${this.position.y}px`,
        };
      },
    },
  };
  </script>
  
  <style scoped>
  .space-invader {
    position: absolute;
    /* Adjust these as needed to fit your game's design */
    width: 50px;
    height: 50px;
  }
  .space-invader img {
    width: 100%;
    height: auto;
  }
  </style>
  