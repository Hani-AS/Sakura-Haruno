<template>
  <div class="main-container">
    <NavBar />
    <router-view />
  </div>
</template>

<script>
import NavBar from "./components/nav/NavBar.vue";
export default {
  name: "App",
  components: {
    NavBar,
  },
};
</script>

<style lang="scss">
html,
body {
  font-family: "Poppins", sans-serif;
  color: #2c2851;
}
.main-container {
  height: 100vh;
  width: 100%;
  background: rgb(255, 244, 245);
  background: linear-gradient(
    180deg,
    rgba(255, 244, 245, 1) 0%,
    rgba(251, 251, 251, 1) 100%
  );
}
</style>
