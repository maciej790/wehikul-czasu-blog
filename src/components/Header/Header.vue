<template>
  <header class="header">
    <div class="header__top">
      <div class="logo"></div>
      <Icon
        @handleChangeMenuState="isMenuOpen = !isMenuOpen"
        :isMenuOpen="isMenuOpen"
        v-if="!isMenuOpen"
      />
    </div>
    <div class="header__down" :class="{ open: isMenuOpen }">
      <Icon
        @handleChangeMenuState="isMenuOpen = !isMenuOpen"
        :isMenuOpen="isMenuOpen"
      />
      <h2 class="header__motto">
        Zwyciężcy piszą <span class="red">Historię</span> na nowo
      </h2>
      <Navigate />
    </div>
  </header>
</template>

<script setup>
import Navigate from "./Navigate.vue";
import Icon from "./Icon.vue";
import { ref } from "vue";

const isMenuOpen = ref(false);
</script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";
.header {
  width: 100%;
  margin: 0 0 3rem 0;
  display: flex;
  flex-direction: column;
  position: sticky;
  top: 0;
  left: 0;
  z-index: 999;
  .header__top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    line-height: 3rem;

    .logo {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 5rem;
      height: 5rem;
      color: white;
      background: url("../../assets/images/logo.jpg");
      background-position: center;
      background-size: cover;

      .logo__img {
        width: 100%;
        height: 100%;
      }
    }
  }

  .header__down {
    width: 100%;
    background: $mbile-nav-bg;
    padding: 2rem 1rem 0 1rem;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    position: fixed;
    min-height: 100vh;
    top: 0;
    left: 0;
    opacity: 0;
    transform: scale(0);
    transition: opacity 0.2s ease-in-out;

    .header__motto {
      width: 100%;
      text-align: center;
      margin: 2rem 0 0 0;

      .red {
        color: $red-main-color;
      }
    }
    &.open {
      transform: scale(1);
      opacity: 1;
      transition: opacity 0.1s ease-in-out;
    }
  }
}
</style>
