<template>
    <div class="contact-form content-box">
        <div class="contact-form__title-box">
            <svg class="svg-icon contact-form__mail-icon" viewBox="0 0 20 20">
                <path d="M17.388,4.751H2.613c-0.213,0-0.389,0.175-0.389,0.389v9.72c0,0.216,0.175,0.389,0.389,0.389h14.775c0.214,0,0.389-0.173,0.389-0.389v-9.72C17.776,4.926,17.602,4.751,17.388,4.751 M16.448,5.53L10,11.984L3.552,5.53H16.448zM3.002,6.081l3.921,3.925l-3.921,3.925V6.081z M3.56,14.471l3.914-3.916l2.253,2.253c0.153,0.153,0.395,0.153,0.548,0l2.253-2.253l3.913,3.916H3.56z M16.999,13.931l-3.921-3.925l3.921-3.925V13.931z"></path>
            </svg>
            <h2 class="contact-form__title">Contact</h2>
        </div>
        <form action="https://www.form-data.com/_functions/submit/b3iz0s4dl6wt31ab4r61b" method="post">
            <div class="contact-form__content">
                <label for="firstname">First name</label>
                <input type="text" name="firstname" id="firstname"/>
            </div>
            <div class="contact-form__content">
                <label for="email">Email</label>
                <input type="text" name="email" id="email"/>

            </div>
            <div class="contact-form__content">
                <label for="content">Content</label>
                <input type="textarea" name="content" id="content"/>
            </div>
            <div class="g-recaptcha contact-form__content"
                 data-sitekey="6Lel4Z4UAAAAAOa8LO1Q9mqKRUiMYl_00o5mXJrR"></div>
            <button class="contact-form__link contact-form__content" type="submit">Submit</button>
        </form>
    </div>

</template>

<script>
    export default {
        name: "Contact"
    }
</script>

<style lang="scss">
    .contact-form {
        max-width: 80%;
        &__title-box {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        &__title {
            margin-top: 0;
        }
        &__mail-icon {
            margin-bottom: 20px;
            margin-right: 10px;
        }
        &__link {
            margin-right: .7em;
            font-size: .8em;
            color: var(--title-color);
            text-decoration: none;
            background-color: var(--bg-color);
            padding: .5em;
            border-radius: var(--radius);
            border-width: 0;

            &:hover {
                box-shadow: 0 0 10px 0 var(--title-color);
            }
        }
    }
</style>
