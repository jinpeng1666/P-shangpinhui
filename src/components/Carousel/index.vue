<template>
  <div class="swiper-container" ref="mySwiper">
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="carousel in list" :key="carousel.id">
        <img :src="carousel.imgUrl" />
      </div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>

    <!-- 如果需要导航按钮 -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>

<script>
import Swiper from "swiper";

export default {
  name: "Carsousel",
  props: ["list"],
  watch: {
    list: {
      handler(newValue, oldValue) {
        immediate: true,
          this.$nextTick(() => {
            var mySwiper = new Swiper(this.$refs.mySwiper, {
              loop: true,

              pagination: {
                el: ".swiper-pagination",
              },

              navigation: {
                nextEl: ".swiper-button-next",
                prevEl: ".swiper-button-prev",
              },
            });
          });
      },
    },
  },
};
</script>

<style>
</style>