<template>
  <div class="item-wrapper">
    <div class="img-wrapper">
      <v-lazy-image
        :src="require(`../../assets/${props.item.img}.webp`)"
        :src-placeholder="
          require(`../../assets/${props.item.placeholder}.webp`)
        "
      />
      <slot />
    </div>
    <h4>{{ item.title }}</h4>
    <p v-if="item.content">{{ item.content }}</p>
    <img
      v-if="item.logo"
      :src="require(`../../assets/${item.logo}.png`)"
      loading="lazy"
      alt=""
      class="design-logo"
    />
  </div>
</template>

<script>
import VLazyImage from "v-lazy-image";
export default {
  props: {
    item: Object,
  },
  setup: (props) => {
    return { props };
  },
  components: {
    VLazyImage,
  },
};
</script>

<style lang="scss">
.v-lazy-image {
  opacity: 0;
  transition: opacity 2s;
}
.v-lazy-image-loaded {
  opacity: 1;
}
</style>
