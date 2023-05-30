<template>
  <Layout>
    <main class="posts">
      <RecentPosts />
      <DailyPost />
      <SecondWarPost />
    </main>
  </Layout>
</template>

<page-query>


</page-query>

<script setup>
import RecentPosts from "../components/MainPosts/RecentPosts.vue";
import DailyPost from "../components/MainPosts/DailyPost.vue";
import SecondWarPost from "../components/MainPosts/SecondWarPost.vue";
</script>

<style>
.posts {
  width: 100%;
}
</style>
