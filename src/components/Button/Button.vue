<template>
  <button class="button">{{ props.title }}</button>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
});
</script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";

.button {
  width: 50%;
  height: 40px;
  padding: 5px;
  background: $red-main-color;
  color: $bg-color;
  border: none;
  border-radius: 10px;
  outline: none;
  font-size: 1rem;
  letter-spacing: 1px;
  font-weight: bold;

  @media only screen and (min-width: $desktop) {
    width: 30%;
  }
}
</style>
