<template>
  <Layout>
    <main class="posts">
      <SectionTitle title="Najnowsze artykuły" />
      <section class="recent">
        <PostCard
          v-for="edge in $page.recent.edges"
          :key="edge.node.id"
          :post="edge.node"
        />
      </section>
      <SectionTitle title="Artykuł dnia" />
      <DailySection :data="$page.daily.edges[0].node" />
      <SectionTitle title="II Wojna Światowa - Najnowsze" />
      <section class="secondWar">
        <PostCard
          v-for="edge in $page.secondWar.edges"
          :key="edge.node.id"
          :post="edge.node"
        />
      </section>
    </main>
  </Layout>
</template>

<script setup>
import SectionTitle from "../components/SectionTitle/SectionTitle.vue";
import PostCard from "../components/PostCard/PostCard.vue";
import Button from "../components/Button/Button.vue";
import ClockAndTime from "../components/ClockAndTime/ClockAndTime.vue";
import DailySection from "../components/DailySection/DailySection.vue";
import { computed, onMounted } from "vue";

const firstSentences = computed(() => {
  {
    // const content = $page.daily.edges[0].node.content;
    // const sentences = content.split(". ");
    // const firstThreeSentences = sentences.slice(0, 3).join(". ");
    // return firstThreeSentences;
  }
});
</script>

<page-query>
  query {
    recent: allPost(sortBy: "date", order: DESC, limit: 3) {
      edges {
        node {
          id
          title
          date
          description
          time
          thumbnail
          tags {
            id
            title
          }
        }
      }
    }
  
    daily: allPost(sortBy: "date", order: DESC, limit: 1) {
      edges {
        node {
          id
          title
          date
          description
          time
          thumbnail
          content
          tags {
            id
            title
          }
        }
      }
    }
  
    secondWar: allPost(filter: {tags: {contains: ["II Wojna Światowa"]}} limit: 4) {
      edges {
        node {
          id
          title
          date
          description
          time
          thumbnail
          tags {
            id
            title
          }
        }
      }
    }
  }
  </page-query>

<style lang="scss">
@import "~/assets/styles/_variables.scss";

.posts {
  width: 100%;
  margin: 0;
  padding: 0;

  .recent {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    gap: 45px 0px;
    justify-items: center;
    align-items: center;
  }

  .secondWar {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    gap: 40px 0px;
    justify-items: center;
    align-items: center;
  }
}
</style>
