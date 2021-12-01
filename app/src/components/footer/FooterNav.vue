<template>
  <div class="footer-container">
    <div class="left-container">
      <img src="@/assets/Nav-Logo.png" alt width="50" height="54" />
      <ul>
        <li>Works</li>
        <li>About</li>
        <li>Media</li>
      </ul>
    </div>
    <div class="right-container">
      <img src="@/assets/slack.png" alt="" />
      <img src="@/assets/google.svg" alt="" />
      <img src="@/assets/flickr.svg" alt="" />
      <img src="@/assets/ng.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.footer-container {
  margin-top: 100px;
  height: 200px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  @media (max-width: 800px) {
    flex-direction: column;
    justify-content: center;
  }

  .left-container {
    display: flex;
    flex-wrap: wrap;

    ul {
      display: flex;
      list-style-type: none;
      align-items: center;

      li {
        margin-left: 40px;
        font-weight: 600;
        @media (max-width: 450px) {
          margin-left: 20px;
        }
      }
    }
  }

  .right-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    @media (max-width: 450px) {
      width: 100%;
    }

    img {
      max-width: 50px;
      max-height: 50px;
      margin-right: 30px;
    }
  }
}
</style>
