<template>
  <div id="app">
    <HeaderApp :cartCount="cartCount" />
    <router-view @add-to-cart="updateCart" />
    <footerApp />
  </div>
</template>

<script>
import FooterApp from "./components/headers/FooterApp.vue";
import HeaderApp from "./components/headers/HeaderApp.vue";

export default {
  components: {
    HeaderApp,
    FooterApp,
  },
  data() {
    return {
      cartCount: 0,
    };
  },
  methods: {
    updateCart(item) {
      this.cartCount += item.quantity;
    },
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  padding-top: 75px;
}
html,
body {
  width: 100%;
  height: 100%;
  /* second */
  overflow-x: hidden;
}

body {
  background: #f8f8f8;
}
/* first */
/* .container {
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 40px;
} */
.container {
  width: 100%;
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 16px;
}
@media (max-width: 1000px) {
  .container {
    max-width: 1000px;
  }
}
</style>
