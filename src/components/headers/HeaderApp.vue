<template>
  <header class="header">
    <div class="container desktop-header">
      <HeaderLogo />
      <HeaderNav />
      <HeaderIcons :cartCount="cartCount" />
    </div>
    <HeaderMobile :cartCount="cartCount" />
  </header>
</template>

<script>
import HeaderIcons from "./HeaderIcons.vue";
import HeaderNav from "./HeaderNav.vue";
import HeaderLogo from "./HeaderLogo.vue";
import HeaderMobile from "./HeaderMobile.vue";

export default {
  components: {
    HeaderIcons,
    HeaderNav,
    HeaderLogo,
    HeaderMobile,
  },
  props: {
    cartCount: Number,
  },
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: #fff;
  min-height: 75px;
}

.container {
  max-width: 1400px;
  margin: auto;
  height: 75px;
  padding: 8px 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
@media (max-width: 1000px) {
  .desktop-header {
    display: none;
  }
}
</style>
