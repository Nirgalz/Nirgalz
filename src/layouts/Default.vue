<template>
    <div id="app">

        <header class="header">
            <div class="header__left">
                <!--        <Logo v-if="showLogo" />-->
                <g-link v-show="$route.path !== '/'" to="/">
                    <svg class="svg-icon" viewBox="0 0 20 20">
                        <path d="M18.121,9.88l-7.832-7.836c-0.155-0.158-0.428-0.155-0.584,0L1.842,9.913c-0.262,0.263-0.073,0.705,0.292,0.705h2.069v7.042c0,0.227,0.187,0.414,0.414,0.414h3.725c0.228,0,0.414-0.188,0.414-0.414v-3.313h2.483v3.313c0,0.227,0.187,0.414,0.413,0.414h3.726c0.229,0,0.414-0.188,0.414-0.414v-7.042h2.068h0.004C18.331,10.617,18.389,10.146,18.121,9.88 M14.963,17.245h-2.896v-3.313c0-0.229-0.186-0.415-0.414-0.415H8.342c-0.228,0-0.414,0.187-0.414,0.415v3.313H5.032v-6.628h9.931V17.245z M3.133,9.79l6.864-6.868l6.867,6.868H3.133z"></path>
                    </svg>
                </g-link>
<!--                |-->
<!--                <g-link to="/about">About</g-link>-->
            </div>

<!--            <div class="header__right">-->
<!--                <ToggleTheme />-->
<!--            </div>-->
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
        },
        components: {
            Logo,
            ToggleTheme
        }
    }
</script>

<style lang="scss">
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        min-height: var(--header-height);
        padding: calc(var(--space) /3);
        top: 0;
        z-index: 10;

        &__left,
        &__right {
            display: flex;
            align-items: center;
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
