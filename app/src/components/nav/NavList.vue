<template>
  <ul :class="props.className">
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
</template>
<script>
export default {
  props: {
    className: {
      type: String,
    },
  },
  setup(props) {
    return { props };
  },
};
</script>
<style lang="scss"></style>
