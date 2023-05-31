<template>
  <article class="card" :style="imageStyle">
    <div class="card__belt">
      <div class="belt__top">
        <h2 class="top__title">{{ props.post.title }}</h2>
        <div class="top__data">
          <p class="top__date">{{ props.post.date }}</p>
          <p class="top__time">
            <img
              :src="require(`../../assets/icons/clock.png`)"
              alt="time"
              class="time__clock"
            />
            {{ timeString }}
          </p>
        </div>
      </div>
      <div class="belt__bottom">
        <p class="bottom__description">
          {{ props.post.description }}
        </p>
      </div>
    </div>
  </article>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});

const imageStyle = computed(() => {
  return {
    background: `url('${props.post.thumbnail.src}')`,
    backgroundSize: "cover",
    backgroundPosition: "center",
    backgroundRepeat: "no-repeat",
  };
});

const timeString = computed(() => {
  if (props.post.time == 1) return `${props.post.time} minuta`;
  else if (props.post.time == 2 || props.post.time == 3 || props.post.time == 4)
    return `${props.post.time} minuty`;
  else return `${props.post.time} minut`;
});
</script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";

.card {
  width: 100%;
  border-radius: 10px;
  height: 450px;
  position: relative;

  .card__belt {
    width: 100%;
    background: rgba(0, 0, 0, 0.6);
    border-radius: 0px 0px 10px 10px;
    opacity: 0, 6;
    position: absolute;
    bottom: 0;
    display: flex;
    flex-direction: column;
    font-size: 1.1rem;

    .belt__top {
      width: 100%;
      padding: 10px;

      .top__title {
        color: $red-main-color;
        text-transform: uppercase;
        margin: 0 0 20px 0;
      }

      .top__data {
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-weight: bold;
        .top__date {
        }

        .top__time {
          display: flex;
          align-items: center;
          font-weight: bold;

          .time__clock {
            margin: 0 15px 0 0;
          }
        }
      }
    }

    .belt__bottom {
      width: 100%;
      padding: 10px;

      .bottom__description {
        text-align: justify;
        line-height: 150%;
      }
    }
  }
}
</style>
