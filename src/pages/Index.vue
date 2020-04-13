<template>
  <Layout :show-logo="false">
    <!-- Author intro -->
    <Author :show-title="true" />

    <!-- List posts -->
<!--    <div class="posts">-->
<!--      <PostCard v-for="edge in $page.tags.edges" :key="edge.node.id" :post="edge.node"/>-->
<!--    </div>-->
    <div class="post-all-tags">
      <g-link class="post-tags__link" v-for="edge in $page.tags.edges" :key="edge.node.id" :to="edge.node.path">
        <span>#</span> {{ edge.node.title }}
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
    margin: 1em 0 0;

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
