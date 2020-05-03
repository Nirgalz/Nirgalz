<template>
    <div id="app">

        <header class="header">
            <div class="header__left">
                <h1 class="header__left__site-title">
                    <g-link to="/" id="header__left__site-title__link">Nicolas Hel - full stack developer</g-link>
                </h1>
            </div>

            <div class="header__right">
                <p class="header__right__links">
                    <a href="https://github.com/Nirgalz">
                        <g-image src="../assets/images/GitHub-Mark-Light-64px.png" width="50" height="50"/>
                    </a>
                    <a href="https://www.linkedin.com/in/nicolas-hel/">
                        <g-image src="../assets/images/linkedin-2-icon-18-256.png" width="50" height="50"/>
                    </a>
                </p>
<!--                <ToggleTheme />-->
            </div>
        </header>

        <main class="main">
            <slot/>
        </main>

        <footer class="footer">
            <span class="footer__copyright">Copyright © {{ new Date().getFullYear() }}. </span>
            <span class="footer__links">Powered by <a href="//gridsome.org"> Gridsome </a></span>
        </footer>

    </div>
</template>

<script>
    import Logo from '~/components/Logo.vue'
    import ToggleTheme from '~/components/ToggleTheme.vue'

    export default {
        props: {
            showLogo: {default: true}
        }
    }
</script>

<style lang="scss">
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        /*height: 85px;*/
        padding: calc(var(--space) /3);
        top: 0;
        z-index: 10;
        background-color: var(--bg-content-color);

        &__left {
            &__site-title {
                margin: 0;
                font-size: calc(var(--base-font-size) *1.2);
                a {
                    text-decoration: none;
                }
            }
        }
        &__right {
            display: flex;
            align-items: center;
            &__links {
                margin: 0;
                a {
                    margin: 0 .5em;
                }
                img:hover {
                    box-shadow: 0 0 10px 0 var(--title-color);
                }
                img {
                    border-radius: 50%;
                }
            }

        }

        @media screen and (min-width: 1300px) {
            //Make header sticky for large screens
            position: sticky;
            width: 100%;
        }
    }

    .main {
        margin: 0 auto;
        padding: 1.5vw 15px 0;
    }

    .footer {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: calc(var(--space) / 2);
        text-align: center;
        font-size: .8em;
        color: var(--title-color);

        > span {
            margin: 0 .35em;
        }

        a {
            color: currentColor;
        }
    }
    .svg-icon {
        width: 2em;
        height: 2em;
    }

    .svg-icon path,
    .svg-icon polygon,
    .svg-icon rect {
        fill: var(--link-color);
    }

    .svg-icon circle {
        stroke: var(--link-color);
        stroke-width: 1;
    }

</style>
