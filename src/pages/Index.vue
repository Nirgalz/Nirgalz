<template>
  <Layout :show-logo="false">
    <!-- Author intro -->
    <Author :show-title="true" />
    <div class="post-all-tags">
      <g-link class="post-all-tags__link" v-for="edge in $page.tags.edges" :key="edge.node.id" :to="edge.node.path">
        <span>#{{ edge.node.title }}</span>
      </g-link>
    </div>
  </Layout>
</template>

<page-query>
query {
  tags: allTag{
    edges {
      node {
        id
        title
        path
      }
    }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'
import { SimpleCarouselContainer, SimpleCarouselItem } from 'vue-simple-carousel';

export default {
  components: {
    Author,
    PostCard
  },
  metaInfo: {
    title: 'Home'
  }
}
</script>

<style lang="scss">
  .post-all-tags {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 1% 20% 1% 20%;

    &__link {
      margin-right: .7em;
      font-size: .8em;
      color: currentColor;
      text-decoration: none;
      background-color: var(--bg-content-color);
      color: currentColor!important; //Todo: remove important;
      padding: .5em;
      border-radius: var(--radius);
    }
  }
</style>
