<template>
  <div class="layout">
    <Header />

    <slot />
    <Footer />
  </div>
</template>
<script setup>
import Header from "../components/Header/Header.vue";
import Footer from "../components/Footer/Footer.vue";
</script>
<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style lang="scss">
@import "~/assets/styles/_variables.scss";
.layout {
  min-height: 100vh;
  background: $bg-color;
  color: $white-color;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1.2rem;
  font-size: 0.9rem;

  @media only screen and (min-width: $desktop) {
    padding: 0 4rem 0 4rem;
  }
}
</style>
