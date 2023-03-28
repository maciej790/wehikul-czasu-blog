<template>
  <nav class="nav">
    <ul class="menu">
      <li class="item__link">
        <g-link class="link__tag" to="/">Home</g-link>
      </li>
      <li class="item__link" @click="isSubMenuOpen = !isSubMenuOpen">
        <g-link class="link__tag"
          >Blog
          <img
            class="link__icon"
            src="../../assets/icons/menu-down.png"
            alt="arrow"
        /></g-link>
      </li>

      <ul class="subMenu" v-for="(subItem, index) in subMenuItems" :key="index">
        <li v-if="isSubMenuOpen" class="item__link">
          <g-link class="link__tag" :to="subItem.path">{{
            subItem.label
          }}</g-link>
        </li>
      </ul>
      <li class="item__link">
        <g-link class="link__tag" to="/o_autorze">O autorze</g-link>
      </li>
      <li class="item__link">
        <g-link class="link__tag" to="/kontakt">Kontakt</g-link>
      </li>
    </ul>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const subMenuItems = ref([
  { label: "Przed I WŚ", path: "/przed_i_ws" },
  { label: "Przed I WŚ", path: "/przed_i_ws" },
  { label: "I WŚ", path: "/i_ws" },
  { label: "II WŚ", path: "/ii_ws" },
  { label: "Świat po II WŚ", path: "/swiat_po_ii_ws" },
  { label: "Wszystko", path: "/wszystko" },
]);

const isSubMenuOpen = ref(false);
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

  .menu {
    width: 100%;
    padding: 0 0 0 2rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;

    .item__link {
      font-size: 1.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 1rem 0 1rem 0;

      .link__tag {
        color: $white-color;
        text-decoration: underline;
      }

      .link__icon {
        text-align: center;
        margin: 0.3rem 0 0 0.5rem;
      }
    }

    .subMenu {
      margin: 0 0 0 1rem;
      .link__tag {
        text-decoration: none;
      }
    }
  }
}
</style>
