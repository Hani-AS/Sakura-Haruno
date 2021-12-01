<template>
  <div class="list-wrapper">
    <BaseListItem v-for="item in items" :key="item.title" :item="item" />
  </div>
</template>

<script>
import BaseListItem from "./BaseListItem.vue";
import { worksList } from "../../data.js";
export default {
  setup: () => {
    const items = worksList;
    return { items };
  },
  components: { BaseListItem },
};
</script>

<style lang="scss" scoped>
.list-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  @media (max-width: 750px) {
    grid-template-columns: 1fr;
  }
  gap: 50px 50px;
  margin-top: 40px;

  :deep .item-wrapper {
    display: flex;
    flex-direction: column;

    img {
      display: block;
      width: 100%;
      max-width: 100%;
      /* height: auto; */
      max-height: 450px;
      @media (max-width: 850px) {
        height: 350px;
      }
      object-fit: cover;
      aspect-ratio: attr(width) / attr(height);
    }

    h4 {
      font-size: 36px;
      margin: 30px 0;
      @media (max-width: 750px) {
        margin: 20px 0;
      }
      @media (max-width: 450px) {
        font-size: 20px;
        margin: 10px 0;
      }
    }

    p {
      font-size: 20px;
      color: gray;
      max-width: 40ch;
      @media (max-width: 450px) {
        font-size: 14px;
      }
    }
  }

  @media (min-width: 1000px) {
    :deep .item-wrapper:first-child {
      grid-row: 1 / span 6;
      img {
        max-height: 600px;
      }
    }
    :deep .item-wrapper:nth-child(2) {
      grid-row: 1 / span 4;
    }
    :deep .item-wrapper:nth-child(3) {
      grid-row: 7 / span 4;
      P {
        margin-bottom: 30px;
      }
    }
    :deep .item-wrapper:nth-child(4) {
      grid-row: 5 / span 6;
      img {
        max-height: 600px;
      }
    }
  }
}
</style>
