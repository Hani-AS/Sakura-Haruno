<template>
  <div class="logos-wrapper">
    <img class="logo" src="@/assets/google.svg" alt="" />
    <img class="logo" src="@/assets/flickr.svg" alt="" />
    <img class="logo" src="@/assets/ng.svg" alt="" />
    <img class="logo" src="@/assets/slack.png" alt="" />
  </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.logos-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-top: 100px;
  @media (max-width: 750px) {
    margin-top: 60px;
  }
  @media (max-width: 450px) {
    margin-top: 20px;
  }

  .logo {
    max-width: 120px;
    @media (max-width: 750px) {
      max-width: 80px;
      margin: 0;
    }
    @media (max-width: 450px) {
      max-width: 50px;
    }
  }
}
</style>
