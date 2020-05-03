<template>
    <div class="contact-form content-box">
        <div v-if="errors.length">
            <b>Please correct the following error(s):</b>
        <ul>
            <li v-for="error in errors">{{ error }}</li>
        </ul>
        </div>
        <div v-if="!isFormShow">
            Thanks for contacting me, I'll get in touch as soon as I can.
        </div>
        <div id="form" v-if="isFormShow">
            <form action="https://www.form-data.com/_functions/submit/b3iz0s4dl6wt31ab4r61b"
                  method="post"
            >
                <div>
                    <label class="contact-form__label" for="firstname">First name</label>
                    <br>
                    <input
                            class="contact-form__input"
                            type="text"
                            v-model="firstname"
                            id="firstname"
                            name="firstname"
                            required
                    />
                </div>
                <div>
                    <label class="contact-form__label" for="email">Email</label>
                    <br>
                    <input
                            class="contact-form__input"
                            type="text"
                            v-model="email"
                            name="email"
                            id="email"
                            required
                    />

                </div>
                <div>
                    <label class="contact-form__label" for="content">Content</label>
                    <br>
                    <textarea
                            class="contact-form__input"
                            name="content"
                            id="content"
                            v-model="content"
                            rows="12"
                            required
                    />
                </div>
                <br>
<!--                            <div class="g-recaptcha contact-form__content"-->
<!--                                 data-sitekey="6Lel4Z4UAAAAAOa8LO1Q9mqKRUiMYl_00o5mXJrR"></div>-->
                <button class="contact-form__link contact-form__submit" type="submit">Submit</button>
            </form>
        </div>

    </div>

</template>

<script>
    export default {
        name: "Contact",
        data() {
            return {
                errors: [],
                firstname: null,
                email: null,
                content: null,
                isFormShow : true
            }
        },
        methods:{
            checkForm: function (e) {
                this.errors = [];

                if (!this.firstname) {
                    this.errors.push('Name required.');
                }
                if (!this.email) {
                    this.errors.push('Mail required.');
                }
                if (!this.content) {
                    this.errors.push('Content required.');
                }
                if (!this.email.includes('@')) {
                    this.errors.push('Correct email required.');
                }

                if (this.errors.length !== 0) {
                    this.isFormShow = true;
                    e.preventDefault();
                }
                else {
                    this.isFormShow = false;
                }
            }
        }
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
        &__input {
            width: 100%;
            background-color: rgb(134, 146, 153);
            resize: none;
        }
        &__label {
            color: var(--title-color);
        }
        &__submit {
            width: 100%;
        }
    }
</style>
