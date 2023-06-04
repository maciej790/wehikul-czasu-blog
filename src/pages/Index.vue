<template>
  <Layout>
    <main class="posts">
      <SectionTitle title="Najnowsze artykuły" />
      <section class="recent">
        <PostCard
          class="recent__card"
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
          class="secondWar__card"
          v-for="edge in $page.secondWar.edges"
          :key="edge.node.id"
          :post="edge.node"
        />
      </section>
      <SectionTitle title="Reszta artykułów" />
      <section class="other">
        <PostCard
          v-for="edge in $page.other.edges"
          :key="edge.node.id"
          :post="edge.node"
        />
      </section>
      <div class="paginatiom">
        <Button title="Zobacz wszystkie" class="btn" />
      </div>
    </main>
  </Layout>
</template>

<script setup>
import SectionTitle from "../components/SectionTitle/SectionTitle.vue";
import PostCard from "../components/PostCard/PostCard.vue";
import DailySection from "../components/DailySection/DailySection.vue";
import Button from "../components/Button/Button.vue";
</script>

<page-query>
  query  {
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

    other: allPost(sortBy: "date", order: DESC, skip: 3, limit: 12) {
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
  width: 90%;
  margin: 0;
  padding: 0;

  @media only screen and (min-width: $desktop) {
    font-size: 1rem;
    width: 85%;
  }

  @media only screen and (min-width: $high-desktop) {
    font-size: 1rem;
    width: 70%;
  }

  .recent {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    gap: 45px 0px;
    justify-items: center;
    align-items: center;
    position: relative;

    @media only screen and (min-width: $desktop) {
      .recent__card:nth-of-type(1) {
        grid-row-start: 1;
        grid-column-start: 1;
        grid-row-end: 3;
        grid-column-end: 2;
        height: 100%;

        .card__belt {
          min-height: 150px;
        }

        .belt__top {
          flex-direction: row;
          align-items: flex-start;
        }

        .top__title {
          width: 65%;
          margin: 0;
        }
      }

      .recent__card:nth-of-type(2) {
        grid-row-start: 1;
        grid-column-start: 2;

        grid-row-end: 2;
        grid-column-end: 3;
      }

      .recent__card:nth-of-type(3) {
        grid-row-start: 2;
        grid-column-start: 2;

        grid-row-end: 3;
        grid-column-end: 3;
      }
    }

    @media only screen and (min-width: $desktop) {
      grid-template-rows: 1fr 1fr;
      grid-template-columns: 1fr 1fr;

      gap: 40px;
      margin: 0 0 100px 0;
    }
  }

  .secondWar {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    gap: 40px 0px;
    justify-items: center;
    align-items: center;

    @media only screen and (min-width: $desktop) {
      grid-template-rows: 1fr 1fr;
      grid-template-columns: 1fr 1fr;

      gap: 40px;
      margin: 0 0 100px 0;

      .secondWar__card {
        width: 100%;
      }
    }
  }

  .other {
    display: grid;
    grid-template-columns: 1fr;
    gap: 40px 40px;
    margin: 0 0 2rem 0;

    @media only screen and (min-width: $desktop) {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 40px 40px;
      justify-items: center;
      align-items: center;
    }
  }

  .paginatiom {
    width: 100%;
    display: flex;
    justify-content: center;

    .btn {
      width: 50%;

      @media only screen and (min-width: $desktop) {
        width: 15%;
      }
    }
  }
}
</style>
