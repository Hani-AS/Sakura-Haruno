<template>
  <div class="header-wrapper">
    <div class="sub-title-wrapper">
      <h4 class="sub-title">— &nbsp;&nbsp;<slot name="sub-title" /></h4>
    </div>
    <div class="title-btn-wrapper">
      <h2 class="main-title">
        <slot name="main-title" />
      </h2>
      <slot name="button" />
      <slot name="content" />
      <slot name="link" />
    </div>
  </div>
</template>

<script>
import { computed } from "@vue/reactivity";
export default {
  props: {
    noSubTitle: Boolean,
    isCentered: Boolean,
  },
  setup: (props) => {
    const cssProp = computed(() => {
      const display = props.noSubTitle ? "none" : "block";
      const column = props.isCentered && "column";

      return { display, column };
    });
    return { cssProp };
  },
};
</script>

<style lang="scss" scoped>
.header-wrapper {
  margin-top: 100px;
  @media (max-width: 750px) {
    margin-top: 60px;
  }

  .sub-title {
    display: v-bind("cssProp.display");
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 30px;
  }

  .title-btn-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    position: relative;
    flex-direction: v-bind("cssProp.column");
    align-items: center;

    .main-title {
      font-size: 64px;
      margin-right: 20px;
      @media (max-width: 750px) {
        font-size: 42px;
      }
      @media (max-width: 450px) {
        font-size: 32px;
      }
    }
    :deep .content {
      font-size: 14px;
      color: gray;
      font-weight: 600;
      margin: 15px;
    }

    :deep .link-button {
      color: #8c6af5;
      font-weight: 600;
    }
    .fa-arrow-right {
      margin-left: 10px;
    }
  }
}
</style>
