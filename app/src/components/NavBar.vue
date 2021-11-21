<template>
  <header>
    <nav>
      <router-link class="home-link" :to="{ name: 'Home' }">
        <div class="logo">
          <img src="@/assets/Nav-Logo.png" alt />
          <span>HARUNO</span>
        </div>
      </router-link>
      <ul v-show="!mobile" class="navigation">
        <li>
          <router-link class="link" :to="{ name: '' }">Works</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: '' }">About</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: '' }">Media</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: '' }">Contact</router-link>
        </li>
      </ul>
      <div class="icon">
        <i
          v-if="mobile"
          class="fa-solid fa-bars"
          :class="{ 'icon-active': mobileNav }"
          @click="toggleMobileNav"
        ></i>
      </div>
      <transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav">
          <li>
            <router-link class="link" :to="{ name: '' }">Works</router-link>
          </li>
          <li>
            <router-link class="link" :to="{ name: '' }">About</router-link>
          </li>
          <li>
            <router-link class="link" :to="{ name: '' }">Media</router-link>
          </li>
          <li>
            <router-link class="link" :to="{ name: '' }">Contact</router-link>
          </li>
        </ul>
      </transition>
    </nav>
  </header>
</template>
<script>
import { ref, onUnmounted } from "vue";
export default {
  name: "NavBar",
  setup() {
    const mobile = ref(null);
    const mobileNav = ref(null);
    const windowWidth = ref(null);

    const toggleMobileNav = () => {
      mobileNav.value = !mobileNav.value;
    };

    const checkScreen = () => {
      windowWidth.value = window.innerWidth;
      if (windowWidth.value < 750) {
        mobile.value = true;
      } else {
        mobile.value = false;
        mobileNav.value = false;
      }
    };

    window.addEventListener("resize", checkScreen);
    checkScreen();
    onUnmounted(() => {
      window.removeEventListener("resize", checkScreen);
    });

    return { mobile, mobileNav, toggleMobileNav };
  },
};
</script>
<style lang="scss" scoped>
header {
  width: 100%;
  position: fixed;

  nav {
    display: flex;
    position: relative;
    flex-direction: row;
    justify-content: space-between;
    padding: 30px 0 12px 0;
    transition: 0.5s ease all;
    width: 90%;
    margin: 0 auto;
    @media (min-width: 1140px) {
      max-width: 1140px;
    }

    .home-link {
      color: #2c2851;
    }

    ul,
    .link,
    .home-link {
      list-style: none;
      text-decoration: none;
    }

    li {
      font-weight: 600;
      margin-left: 46px;
    }

    .link {
      font-size: 16px;
      transition: 0.5s ease all;
      padding-bottom: 4px;
      border-bottom: 1px solid transparent;
      color: #2c2851;

      &:hover {
        border-color: #2c2851;
      }
    }

    .logo {
      display: flex;
      align-items: center;

      img {
        margin-top: 10px;
        width: 50px;
      }
      span {
        font-size: 16px;
        font-weight: 600;
        margin-left: 15px;
      }
    }

    .navigation {
      display: flex;
      align-items: center;
      flex: 1;
      justify-content: flex-end;
    }
    .icon {
      display: flex;
      align-items: center;
      i {
        cursor: pointer;
        font-size: 24px;
        transition: 0.8s ease all;
      }
    }
    .icon-active {
      transform: rotate(180deg);
    }
    .dropdown-nav {
      display: flex;
      flex-direction: column;
      position: fixed;
      width: 100%;
      max-width: 250px;
      height: 100%;
      background-color: #fff;
      top: 0;
      left: 0;
      li {
        margin-left: 10px;
        margin-top: 20px;
      }
    }
    .mobile-nav-enter-active,
    .mobile-nav-leave-active {
      transition: 0.8s ease all;
    }
    .mobile-nav-enter-from,
    .mobile-nav-leave-to {
      transform: translateX(-250px);
    }
    .mobile-nav-enter-to {
      transform: translateX(0);
    }
  }
}
</style>
