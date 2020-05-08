<template>
    <div class="post-card content-box" :class="{'post-card--has-poster' : post.poster}" @click="onClickCard(post)">
        <div class="post-card__content">
            <h4 class="post-card__title" v-html="post.title"/>
            <PostMeta class="post-card__meta" :post="post"/>
            <p class="post-card__description" v-html="post.description"/>

            <g-image alt="Cover image" v-if="post.cover_image" class="post-card__image" :src="post.cover_image"/>
            <div class="post__content" v-html="post.content" />
            <div class="post-card__footer">


            </div>
            <PostTags class="post-card__tags" :post="post"/>
        </div>
    </div>
</template>

<script>
    import PostMeta from '~/components/PostMeta'
    import PostTags from '~/components/PostTags'

    export default {
        components: {
            PostMeta,
            PostTags
        },
        props: ['post'],
        methods : {
            onClickCard() {
                this.$emit("closeproject");
            }
        }
    }
</script>

<style lang="scss" scoped>


        .post-card {
        position: relative;
        max-width: 60%;
        padding: 30px;
        margin: auto;
        &__header {
            margin-left: calc(var(--space) * -1);
            margin-right: calc(var(--space) * -1);
            margin-bottom: calc(var(--space) / 2);
            margin-top: calc(var(--space) * -1);
            overflow: hidden;
            border-radius: var(--radius) var(--radius) 0 0;

            &:empty {
                display: none;
            }
        }

        &__description {
            font-size: var(--content-text);
        }

        &__footer {
            margin-left: var(--space);
            margin-right: var(--space);
            margin-bottom: var(--space);
            margin-top: var(--space);
            overflow: hidden;
            border-radius: var(--radius) var(--radius) 0 0;

            &:empty {
                display: none;
            }
        }


        /*&__image {*/
        /*    margin: 0 10px 5px 10px;*/

        /*}*/

        &__title {
            margin-top: 0;
        }

        &:hover {
            box-shadow: 0 0 10px 0 var(--link-color);
            cursor: pointer;
        }


        &__tags {
            z-index: 1;
            position: relative;

        }

        &__meta {
            position: absolute;
            right: calc(var(--space) * 1);
            top: calc(var(--space) * 1);
        }
    }

        @media only screen and (max-width: 800px) {
            .post-card {
                max-width: 100%;
            }
        }
</style>
