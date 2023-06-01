<template>
  <section class="daily">
    <div class="daily__top">
      <PostCard :post="data" :isDaily="true" />
    </div>
    <div class="daily__bottom">
      <h1 class="bottom__title">{{ data.title }}</h1>
      <ClockAndTime :data="data" />
      <div class="bottom__space" style="margin: 0 0 40px 0;"></div>
      <div class="bottom__sentence">
        <p v-html="firstSentences"></p>
      </div>
      <Button title="Czytaj dalej" />
    </div>
  </section>
</template>

<script setup>
import PostCard from "../PostCard/PostCard.vue";
import ClockAndTime from "../ClockAndTime/ClockAndTime.vue";
import Button from "../Button/Button.vue";
import { computed } from "vue";
const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
});

const firstSentences = computed(() => {
  const content = props.data.content;
  const sentences = content.split(".");
  const firstThreeSentences = sentences.slice(0, 3);
  const excerpt = firstThreeSentences.join(". ") + ".";
  return `${excerpt}${" "}(...)`;
});
</script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";

.daily {
  display: flex;
  flex-direction: column;
  .daily__top {
  }

  .daily__bottom {
    width: 100%;
    margin: 40px 0 0 0;

    .bottom__title {
      color: $red-main-color;
      text-transform: uppercase;
      margin: 0 0 7px 0;
      font-size: 1.2rem;
    }

    .bottom__description {
      text-align: justify;
      line-height: 150%;
      margin: 20px 0 20px 0;
    }

    .bottom__sentence {
      margin: 0 0 50px 0;
      text-align: justify;
      line-height: 150%;
    }

    .bottom_data {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: bold;
      margin: 0 0 50px 0;

      .data__date {
      }

      .data__time {
        display: flex;
        justify-content: space-between;
        align-items: center;

        .time__clock {
          margin: 0 15px 0 0;
        }
      }
    }
  }
}
</style>
