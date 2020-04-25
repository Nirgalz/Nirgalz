<template>
   <div class="post-tags">
   		<g-link class="post-tags__link" v-for="tag in post.tags" :key="tag.id" :to="tag.path">
   			<span>#</span> {{ tag.title }}
   		</g-link>
    </div>
</template>

<script>
export default {
  props: ['post']
}
</script>

<style lang="scss">
.post-tags {
  margin: 1em 0 0;

  &__link {
  	margin-right: .7em;
  	font-size: .8em;
  	color: var(--title-color);
  	text-decoration: none;
  	background-color: var(--bg-color);
  	padding: .5em;
  	border-radius: var(--radius);
	  &:hover {
		  box-shadow: 0 0 10px 0 var(--title-color);
		  background-color: var(--bg-color);
	  }
  }
}
</style>
