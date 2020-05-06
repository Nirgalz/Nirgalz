<template>
    <div class="post-card content-box" :class="{'post-card--has-poster' : post.poster}">
        <div class="post-card__content">
            <h4 class="post-card__title" v-html="post.title"/>
            <PostMeta class="post-card__meta" :post="post"/>
            <p class="post-card__description" v-html="post.description"/>

            <div class="post-card__link"
                    @click="onClickCard(post)"
            >
                Link
            </div>

            <g-image alt="Cover image" v-if="post.cover_image" class="post-card__image" :src="post.cover_image"/>
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
            onClickCard(post) {
                this.$emit("project", post);
            }
        }
    }
</script>

<style lang="scss" scoped>
    .post-card {
        margin-bottom: var(--space);
        position: relative;
        height: 360px;

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
        &__image {
            overflow: hidden;
            height: 135px;
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
            box-shadow: 0 0 10px 0 var(--title-color);
            cursor: pointer;
        }

        &__tags {
            z-index: 1;
            position: relative;

        }

        &__link {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.0;
            overflow: hidden;
            text-indent: -9999px;
            z-index: 0;
        }
        &__meta {
            position: absolute;
            right: calc(var(--space) * 1);
            top: calc(var(--space) * 1);
        }
    }
</style>
