<template>
  <div>
    <div class="box" @click="handleClick" :class="{ popped: isPopped }">
      <div class="box-tape">
        <div class="box-tape-left"></div>
        <div class="box-tape-right"></div>
        <div class="box-tape-center"></div>
      </div>
      <div class="box-gifts">
        <div class="box-gift-shadow"></div>
      </div>
      <div class="box-gift"></div>
      <div class="box-star box-star-1"></div>
      <div class="box-star box-star-2"></div>
      <div class="box-star box-star-3"></div>
      <div class="box-star box-star-4"></div>
      <div class="box-star box-star-5"></div>
    </div>
    <div v-if="showCard" class="bunny">
      <img
        src="https://static.vecteezy.com/system/resources/previews/016/327/326/original/cute-rabbit-characters-png.png"
      />
    </div>
    <div v-if="showCard" class="bunny2">
      <img
        src="https://static.vecteezy.com/system/resources/previews/016/327/322/non_2x/cute-rabbit-characters-png.png"
      />
    </div>
    <div v-if="showCard" class="card">
      <p>happy birthday syed :3 i hope you enjoy ur day</p>
      <p>wishing you a wonderful year ahead</p>
    </div>
    <div v-if="showConfetti" class="confetti-container">
      <div
        v-for="n in 100"
        :key="n"
        class="confetti"
        :style="getConfettiStyle()"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPopped: false,
      showCard: false,
      showConfetti: false,
    };
  },
  methods: {
    handleClick() {
      this.isPopped = true;
      setTimeout(() => {
        this.showConfetti = true;
        this.showCard = true;
        setTimeout(() => {
          this.showConfetti = false; // Hide confetti after some time
        }, 5000); // Adjust timing as needed
      }, 500); // Adjust timing as needed
    },
    getConfettiStyle() {
      const colors = ["red", "blue", "yellow", "green", "orange", "purple"];
      const size = Math.random() * 10 + 5;
      const left = Math.random() * 100;
      const delay = Math.random() * 2;
      const color = colors[Math.floor(Math.random() * colors.length)];
      return {
        backgroundColor: color,
        width: `${size}px`,
        height: `${size * 2}px`,
        left: `${left}%`,
        animationDelay: `${delay}s`,
      };
    },
  },
};
</script>
