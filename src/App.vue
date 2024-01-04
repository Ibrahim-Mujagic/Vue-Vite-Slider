<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import SliderContComponent from "./components/SliderContComponent.vue";
export default {
  name: "App",
  components: {
    HeaderComponent,
    SliderContComponent,
  },
};
</script>

<template>
  <HeaderComponent />
  <div class="container-general">
    <SliderContComponent />
  </div>
</template>

<style lang="scss">
.container-general {
  height: calc(100vh - 90px);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
