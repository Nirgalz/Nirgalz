<template>
    <Layout :show-logo="false">
        <h2 class="index-title">
            Projects
        </h2>
        <div class="post-all-tags">
            <div class="post-all-tags__link" v-for="edge in $page.tags.edges" :key="edge.node.id"
                 @click="filterTags(edge.node.id)"
                    >
                <span>#{{ edge.node.title }}</span>
            </div>

        </div>
        <div class="posts">
            <PostCard v-for="edge in posts" :key="edge.node.id" :post="edge.node"
                      @project="onClickedProject"
                      v-if="project === null && hasTag(edge.node)"
            />

            <FullPost
                    v-if="project !== null"
                    :post="project"
                    @closeproject="onCloseProject"

            />


        </div>

        <div class="about-box">
            <div class="title-box">
                <h2>About</h2>
            </div>
            <about></about>
        </div>

        <div class="contact-box">

            <div class="title-box">
                <!--                <svg class="svg-icon contact-form__mail-icon" viewBox="0 0 20 20">-->
                <!--                    <path d="M17.388,4.751H2.613c-0.213,0-0.389,0.175-0.389,0.389v9.72c0,0.216,0.175,0.389,0.389,0.389h14.775c0.214,0,0.389-0.173,0.389-0.389v-9.72C17.776,4.926,17.602,4.751,17.388,4.751 M16.448,5.53L10,11.984L3.552,5.53H16.448zM3.002,6.081l3.921,3.925l-3.921,3.925V6.081z M3.56,14.471l3.914-3.916l2.253,2.253c0.153,0.153,0.395,0.153,0.548,0l2.253-2.253l3.913,3.916H3.56z M16.999,13.931l-3.921-3.925l3.921-3.925V13.931z"></path>-->
                <!--                </svg>-->
                <h2>Contact</h2>
            </div>
            <contact></contact>
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
    },
    posts: allPost(filter: { published: { eq: true }}, sortBy: "year" ) {
    edges {
    node {
    title
    path
    year
    tags {
    id
    title
    path
    }
    description
    content
    cover_image
    }
    }
    }
    }
</page-query>

<script>
    import Author from '~/components/Author.vue'
    import PostCard from '~/components/PostCard.vue'
    import Contact from "../components/Contact";
    import About from "../components/About";
    import Default from "../layouts/Default";
    import Post from "../templates/Post";
    import FullPost from "../components/FullPost";

    export default {
        components: {
            FullPost,
            Post,
            Default,
            About,
            Contact,
            Author,
            PostCard
        },
        data() {
            return {
                project: null,
                filteredTag: [],
                posts : {}
            }
        },
        methods: {
            onClickedProject(project) {

                // this.project = project;
                let data = Object.assign({}, this.$route.query);
                data['project'] = project.title;
                this.$router.push({name: 'home', query: data})
            },
            onCloseProject() {
                this.project = null;
                window.scrollTo(0, 0);
                this.$router.push({name: 'home', query: ""})
            },
            filterTags(tag) {
                if (tag === "ALL") {
                    this.resetTags();
                    this.resetPosts();
                }
                else {
                    this.filteredTag = [];
                    this.filteredTag.push(tag);
                    this.filterPosts(tag);
                }
            },
            filterPosts(tag) {
                for (let i = 0 ; i < this.posts.length ; i++) {
                    for (let j = 0; j < this.posts[i].node.tags.length ; j++) {
                        if (this.posts[i].node.tags[j].id === tag) {
                            this.filteredTag.push(this.posts[i].node.tags[j].id)
                        }
                    }
                }
            },
            resetTags() {
                let edges = this.$page.posts.edges;
                for (let i = 0; i < edges.length; i++) {
                    for (let j = 0; j < edges[i].node.tags.length; j++) {
                        if (!this.filteredTag.includes(edges[i].node.tags[j].id)) {
                            this.filteredTag.push(edges[i].node.tags[j].id);
                        }
                    }
                }
            },
            resetPosts() {
                this.posts = this.$page.posts.edges;
            },
            hasTag(node) {
                for (let i = 0 ; i < node.tags.length ; i++) {

                    if (this.filteredTag.includes(node.tags[i].id)) {

                        return true
                    }
                }
                return false;
            }
        },
        updated() {
            if (Object.keys(this.$router.currentRoute.query).length === 0 && this.$router.currentRoute.query.constructor === Object) {
                this.project = null;
            } else {
                let edges = this.$page.posts.edges;
                for (let i = 0; i < edges.length; i++) {
                    if (edges[i].node.title === this.$router.currentRoute.query.project) {
                        this.project = edges[i].node
                    }
                }
            }
        },
        mounted() {
            this.resetTags();
            this.resetPosts();
            this.$page.tags.edges.splice(0,0,{node: {id : "ALL", title: "ALL"}});
        }
    }
</script>

<style lang="scss">
    .post-all-tags {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin: 1% 20% 30px 20%;

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

    .index-title {
        margin-top: 20px;
        text-align: center;
    }

    .title-box {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .contact-box {
        max-width: 1100px;
        margin: auto;
    }

</style>
