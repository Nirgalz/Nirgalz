<template>
   <div class="post-meta">
      {{ post.year }}
    </div>
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
.post-meta {
  font-size: 1em;
    color: var(--title-color);
}
</style>
