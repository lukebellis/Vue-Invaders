<template>
    <div class="space-ship" :style="shipStyle">
      <img src="@/assets/spaceship.png" alt="Spaceship" />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        position: {
          x: 0, // Initial X position
          y: 0, // Initial Y position, adjust based on your game board's layout
        },
      };
    },
    computed: {
      shipStyle() {
        // Use the position data to position the spaceship on the game board
        return {
          left: `${this.position.x}px`,
          bottom: `${this.position.y}px`,
        };
      },
    },
    mounted() {
      window.addEventListener('keydown', this.handleMovement);
    },
    beforeUnmount() { // Updated from beforeDestroy to beforeUnmount
      window.removeEventListener('keydown', this.handleMovement);
    },
    methods: {
      handleMovement(event) {
        // Example movement handler (left and right arrow keys)
        const moveStep = 10; // Adjust the step size as needed
        if (event.key === 'ArrowLeft') {
          this.position.x = Math.max(this.position.x - moveStep, 0); // Move left
        } else if (event.key === 'ArrowRight') {
          this.position.x += moveStep; // Move right
          // Add bounds checking here if needed
        }
        // Implement other movement directions or actions as needed
      },
    },
  };
  </script>
  
  <style scoped>
  .space-ship {
    position: absolute;
    /* Adjust these as needed to fit your game's design */
    width: 60px; 
    height: 60px;
  }
  .space-ship img {
    width: 100%;
    height: auto;
  }
  </style>
  