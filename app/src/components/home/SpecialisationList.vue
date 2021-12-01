<template>
  <div class="list-wrapper">
    <BaseListItem v-for="item in items" :key="item.title" :item="item" />
  </div>
</template>
<script>
import { specialisationItems } from "../../data.js";
import BaseListItem from "./BaseListItem.vue";
export default {
  setup: () => {
    const items = specialisationItems;

    return { items };
  },
  components: {
    BaseListItem,
  },
};
</script>
<style lang="scss" scoped>
.list-wrapper {
  display: flex;
  gap: 30px;
  margin-top: 40px;
  @media (max-width: 750px) {
    gap: 20px;
  }
  @media (max-width: 450px) {
    flex-direction: column;
    gap: 30px;
  }
}
:deep .item-wrapper {
  display: flex;
  flex-direction: column;

  img {
    max-width: 100%;
    height: auto;
    aspect-ratio: attr(width) / attr(height);
    margin-bottom: 40px;
    @media (max-width: 750px) {
      margin-bottom: 20px;
    }
    @media (max-width: 450px) {
      margin-bottom: 5px;
    }
  }
  h4 {
    font-size: 36px;
    @media (max-width: 1000px) {
      font-size: 26px;
    }
    @media (max-width: 750px) {
      font-size: 20px;
    }
  }
}
</style>
