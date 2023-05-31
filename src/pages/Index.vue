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
      <section class="daily">
        <PostCard :post="$page.daily.edges[0].node" />
      </section>
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

<script setup>
import SectionTitle from "../components/SectionTitle/SectionTitle.vue";
import PostCard from "../components/PostCard/PostCard.vue";
</script>

<style lang="scss">
.posts {
  width: 90%;
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
