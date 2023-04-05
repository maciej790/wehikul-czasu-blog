<template>
  <nav class="nav">
    <ul class="nav__menu" v-for="(item, index) in menuItems" :key="index">
      <li class="menu__link">
        <g-link class="link__tag" :to="item.path">{{ item.label }}</g-link>
      </li>
    </ul>
  </nav>
</template>

<page-query>
  
 
</page-query>

<script setup>
import { ref } from "vue";

const menuItems = ref([
  { label: "Home", path: "/" },
  { label: "Artykuły", path: "/artykuly" },
  { label: "O autorze", path: "/o_autorze" },
  { label: "Kontakt", path: "/kontatk" },
]);
</script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";

.nav {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 2rem 0 0 0;

  .nav__menu {
    width: 100%;
    padding: 0 0 0 1rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;

    .menu__link {
      font-size: 1.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 1rem 0 1rem 0;

      .link__tag {
        color: $white-color;
        text-decoration: underline;
      }
    }
  }
}
</style>
