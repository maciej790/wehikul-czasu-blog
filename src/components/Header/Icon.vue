<template>
  <div class="menuIcon" @click="$emit('handleChangeMenuState')">
    <img
      class="icon_img"
      :src="require(`../../assets/icons/${iconSource}.png`)"
    />
  </div>
</template>

<script setup>
import { computed } from "vue";
const props = defineProps({
  isMenuOpen: {
    type: Boolean,
  },
});

const iconSource = computed(() => {
  return props.isMenuOpen ? "close" : "dropdown";
});
</script>

<style lang="scss">
.menuIcon {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 35px;
  height: 35px;

  .icon_img {
    width: 100%;
    height: 100%;
  }
}
</style>
