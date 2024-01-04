<script>
export default {
  name: "ButtonSliderComponent",
  props: {
    icon: String,
    typeButton: String,
  },
  data() {
    return {};
  },
};
</script>
<template>
  <button :class="typeButton" v-html="icon"></button>
</template>

<style lang="scss" scoped>
button {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  border: 1px solid gold;
  background-color: goldenrod;
  color: #fff;
  font-size: 1.2rem;
  position: absolute;
  transform: translateY(-50%);
  cursor: pointer;
  top: 50%;
  &.nextButton {
    right: 5%;
  }
  &.prevButton {
    left: 5%;
  }

  &:hover {
    height: 52px;
    width: 52px;
  }
  &:active {
    box-shadow: 0px 0px 10px rgba(255, 217, 0, 0.646);
  }
}
</style>
