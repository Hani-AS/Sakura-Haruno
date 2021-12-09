<template>
  <div class="button-wrapper">
    <button><slot /> <i class="fas fa-arrow-right" /></button>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  props: {
    isAbsolute: Boolean,
    height: Number,
    width: Number,
  },
  setup: (props) => {
    const cssProp = computed(() => {
      const position = props.isAbsolute ? "absolute" : "static";
      const height = props.height && `${props.height}px`;
      const width = props.width && `${props.width}%`;
      return { position, height, width };
    });
    return { cssProp };
  },
};
</script>

<style lang="scss" scoped>
.button-wrapper {
  display: flex;
  position: v-bind("cssProp.position");
  right: 0;
  bottom: 0;
  width: v-bind("cssProp.width");
  max-width: 200px;
  height: v-bind("cssProp.height");
  background-color: white;
  place-content: center;
  transition: 0.5s ease-in-out;
  @media (min-width: 850px) {
    padding: 10px;
  }

  &:hover {
    background-color: green;
    cursor: pointer;
  }

  button {
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 500;
    width: 100%;
    transition: 0.5s ease-in-out;
    &:hover {
      color: #fff;
    }
    i {
      margin-left: 15px;
    }
  }
}
</style>
