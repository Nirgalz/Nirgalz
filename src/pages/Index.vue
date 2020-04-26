<template>
  <Layout :show-logo="false">
    <!-- Author intro -->
    <Author :show-title="true" />
    <div class="post-all-tags">
      <g-link class="post-all-tags__link" v-for="edge in $page.tags.edges" :key="edge.node.id" :to="edge.node.path">
        <span>#{{ edge.node.title }}</span>
      </g-link>

    </div>
    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
    </div>
    <contact></contact>
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
  },
  posts: allPost(filter: { published: { eq: true }}, sortBy: "year" ) {
  edges {
  node {
  id
  title
  year
  description
  cover_image (width: 770, height: 380, blur: 10)
  path
  tags {
  id
  title
  path
  }
  }
  }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'
import Contact from "../components/Contact";

export default {
  components: {
    Contact,
    Author,
    PostCard
  }
  // ,
  // metaInfo: {
  //   title: 'Home'
  // }
}
</script>

<style lang="scss">
  .post-all-tags {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 1% 20% 70px 20%;

    &__link {
      margin-right: .7em;
      font-size: .8em;
      color: var(--link-color);
      text-decoration: none;
      background-color: var(--bg-content-color);
      padding: .5em;
      border-radius: var(--radius);
      &:hover {
        box-shadow: 0 0 10px 0 var(--title-color);
      }
    }
  }

  .posts {
    display: flex;
    flex-wrap: wrap;
  }
</style>
