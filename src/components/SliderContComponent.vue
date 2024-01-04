<script>
import ButtonSliderComponent from "./ButtonSliderComponent.vue";
import imageData from "../data/data.js";
export default {
  name: "SliderContComponent",
  components: {
    ButtonSliderComponent,
  },
  data() {
    return {
      imageIndex: 0,
      leftIcon: `<i class="fa-solid fa-arrow-left"></i>`,
      rightIcon: `<i class="fa-solid fa-arrow-right"></i>`,
      leftClass: "prevButton",
      rightClass: "nextButton",
      imageData,
      time: "",
    };
  },
  methods: {
    nextPrevSlide(isNext) {
      if (isNext) {
        this.imageIndex++;
        if (this.imageIndex === imageData.length) {
          this.imageIndex = 0;
        }
      } else {
        this.imageIndex--;
        if (this.imageIndex < 0) {
          this.imageIndex = imageData.length - 1;
        }
      }
    },
    startAutoPlay() {
      this.time = setInterval(() => this.nextPrevSlide(true), 1500);
    },
    stopAutoPlay() {
      clearInterval(this.time);
    },
  },
  mounted() {
    this.startAutoPlay();
  },
};
</script>

<template>
  <div @mouseover="stopAutoPlay()" @mouseout="startAutoPlay()" class="slider">
    <div class="image-container">
      <img
        :src="imageData[imageIndex].image"
        :alt="imageData[imageIndex].name"
      />
      <ButtonSliderComponent
        @click="nextPrevSlide(false)"
        :typeButton="leftClass"
        :icon="leftIcon"
      />
      <ButtonSliderComponent
        @click="nextPrevSlide(true)"
        :typeButton="rightClass"
        :icon="rightIcon"
      />
    </div>
    <div class="dots">
      <div
        v-for="(item, index) in imageData"
        :key="index"
        :class="{ dot: true, active: index === imageIndex }"
        @click="imageIndex = index"
      ></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.slider {
  height: 550px;
  width: 75%;
  border: 2px solid gold;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  position: relative;
  .image-container {
    height: 100%;
    width: 100%;
    object-fit: cover;

    img {
      height: 100%;
      width: 100%;
      border-radius: 10px;
      object-fit: cover;
    }
  }
  .dots {
    bottom: 20px;
    height: 60px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0px 10px;
    position: absolute;
    z-index: 2;
    .dot {
      height: 20px;
      width: 20px;
      border-radius: 50%;
      cursor: pointer;
      background-color: gold;
      opacity: 0.4;
      &:hover {
        transform: scale(1.2);
      }
      &.active {
        opacity: 1;
      }
    }
  }
}
</style>
