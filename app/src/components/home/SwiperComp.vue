<template>
  <swiper
    :slides-per-view="1"
    :space-between="50"
    :breakpoints="breakpoints"
    :grabCursor="true"
    :speed="1000"
    class="swiper-container"
  >
    <swiper-slide v-for="item in items" :key="item.img" class="slide">
      <BaseListItem :item="item">
        <BaseButton :isAbsolute="true" :height="60" :width="30"
          >Read</BaseButton
        >
      </BaseListItem></swiper-slide
    >
  </swiper>
</template>

<script>
import { designItems } from "../../data.js";
import BaseListItem from "./BaseListItem.vue";
import BaseButton from "./BaseButton.vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import "../../assets/swiper-bundle.css";
export default {
  components: {
    Swiper,
    SwiperSlide,
    BaseListItem,
    BaseButton,
  },
  setup() {
    const items = designItems;

    const breakpoints = {
      320: {
        slidesPerView: 1.3,
        spaceBetween: 20,
      },
      750: {
        slidesPerView: 2.2,
        spaceBetween: 50,
      },
    };

    return {
      breakpoints,
      items,
      BaseListItem,
    };
  },
};
</script>

<style lang="scss" scoped>
.swiper-container {
  margin-top: 40px;
  width: 100%;
  overflow-x: hidden;
}
.slide {
  :deep .item-wrapper {
    display: flex;
    flex-direction: column;

    .img-wrapper {
      position: relative;
    }

    img {
      display: block;
      max-width: 100%;
      height: auto;
      aspect-ratio: attr(width) / attr(height);
    }
    h4 {
      font-size: 36px;
      margin: 30px 0 20px 0;
      @media (max-width: 1000px) {
        font-size: 26px;
      }
      @media (max-width: 750px) {
        font-size: 20px;
        margin: 20px 0 10px 0;
      }
    }
    p {
      font-size: 16px;
      max-width: 45ch;
      @media (max-width: 450px) {
        font-size: 14px;
      }
    }

    .button-wrapper {
      @media (max-width: 450px) {
        width: 40%;
      }
    }

    .design-logo {
      max-width: 30px;
      padding: 10px;
      background-color: white;
      position: absolute;
      right: 0;
    }
  }
}
</style>
