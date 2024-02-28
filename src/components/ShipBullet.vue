<template>
    <div class="bullet" :style="bulletStyle"></div>
  </template>
  
  <script>
  export default {
    props: {
      // Initial position of the bullet
      initialPosition: {
        type: Object,
        required: true,
      },
    },
    data() {
      return {
        position: this.initialPosition,
      };
    },
    computed: {
      bulletStyle() {
        // Style to position the bullet on the game board
        return {
          left: `${this.position.x}px`,
          top: `${this.position.y}px`,
        };
      },
    },
    mounted() {
      this.moveBullet();
    },
    methods: {
      moveBullet() {
        const moveInterval = setInterval(() => {
          this.position.y -= 5; // Move the bullet up
  
          // Stop moving the bullet if it goes off screen
          if (this.position.y < 0) {
            clearInterval(moveInterval);
            // Consider removing the bullet from the DOM or notifying the parent component
            this.$emit('bulletOffScreen', this.position);
          }
        }, 100); // Adjust timing for bullet speed
      },
    },
  };
  </script>
  
  <style scoped>
  .bullet {
    position: absolute;
    width: 5px; /* Adjust based on your design */
    height: 15px; /* Adjust based on your design */
    background-color: white; /* Bullet color */
    border-radius: 50%; /* Optional, for rounded bullets */
  }
  </style>
  
  