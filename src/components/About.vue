<template>
    <div class="content-box about">
        <div>
            <p>
                After ten years working on computer maintenance, both hardware and software, while developing websites with various CMS as a hobby, I took a u-turn four years ago to go coding full-time.
                I took two courses leading to diplomas in software development. I then worked two years for various service companies on various projects for big clients and am now working as an independent software developer.
            </p>
            <h4 class="about__title">Methodology</h4>
            <p>
                My goal is to identify your needs and develop for you the best solution possible for your specific needs.
                I prefer to work on small iterations and make you part of the development process so that we can get to the best result possible in the least amount of time.
                Having worked with various different technologies, I can make technical choices that will best serve your projects.
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "About"
    }
</script>

<style lang="scss">
    .about {
        max-width: 90%;
        display: flex;
        &__title {
            margin-top: 20px;
         }
    }
</style>
