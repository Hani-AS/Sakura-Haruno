<template>
  <section class="intro-wrapper">
    <div class="info-section">
      <div class="text-wrapper">
        <h2>Sakura haruno</h2>
        <h1>
          Designer &<br />
          Illustrator
        </h1>
        <p>
          Norway based designer who specialised<br />
          in Product design and illustration
        </p>
      </div>
    </div>
    <div class="image-section">
      <div class="img-1">
        <img
          src="@/assets/author.webp"
          src-placeholder="@/assets/author_small.webp"
          alt=""
          width="650"
          height="750"
        />
      </div>
      <div class="img-2">
        <img src="@/assets/intro-2.webp" alt="" width="20" height="750" />
      </div>
      <BaseButton :isAbsolute="true" :height="80" :width="100">
        About Myself
      </BaseButton>
    </div>
  </section>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
  name: "HomeIntro-comp",
  components: {
    BaseButton,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");

.intro-wrapper {
  display: flex;
  @media (max-width: 750px) {
    flex-direction: column;
  }
  position: relative;

  .info-section {
    flex: 1;

    .text-wrapper {
      position: absolute;
      @media (max-width: 750px) {
        position: relative;
      }
      left: 0;
      top: 20%;
      z-index: 1;
      h2 {
        margin-bottom: 25px;
        font-family: "Pacifico", cursive;
        font-size: 36px;
        @media (max-width: 750px) {
          font-size: 24px;
          margin-bottom: 0;
        }
        font-weight: normal;
      }
      h1 {
        font-size: 92px;
        @media (max-width: 750px) {
          font-size: 42px;
        }
        line-height: 1.1;
        background-clip: text;
        -webkit-background-clip: text;
        color: transparent;
        background-image: url("../../assets/intro-2.webp");
        background-position: center;
        background-size: cover;
      }
      p {
        font-size: 20px;
        @media (max-width: 750px) {
          font-size: 14px;
          margin: 5px 0;
        }
        font-weight: 500;
        color: gray;
        margin-top: 40px;
      }
    }
  }

  .image-section {
    display: flex;
    position: relative;
    width: 100%;
    justify-content: flex-end;
    flex: 3;

    .img-1 {
      width: 100%;
      max-width: 650px;
      img {
        width: 100%;
        height: auto;
        aspect-ratio: attr(width) / attr(height);
        display: block;
      }
    }
    .img-2 {
      width: 20px;
      img {
        width: 100%;
        height: 100%;
        aspect-ratio: attr(width) / attr(height);
        object-fit: cover;
      }
    }

    /* .button-wrapper {
      display: flex;
      position: absolute;
      right: 0;
      bottom: 0;
      width: 100%;
      max-width: 200px;
      height: 80px;
      background-color: white;
      place-content: center;
      transition: 0.5s ease-in-out;

      &:hover {
        background-color: green;
        cursor: pointer;
      }
      &:active {
        letter-spacing: 2px;
      }

      button {
        font-weight: 500;
        width: 100%;
        transition: 0.5s ease-in-out;
        &:hover {
          color: #fff;
        }
        i {
          margin-left: 15px;
        }
        &:active {
          letter-spacing: 1px;
          transition: 0.2s ease-in;
        }
      }
    } */
  }
}
</style>
