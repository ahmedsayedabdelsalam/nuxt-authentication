<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <nuxt-link :to="{ name: 'index' }" class="navbar-item">
            <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
            </nuxt-link>

            <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
            </a>
        </div>

        <div id="navbarBasicExample" class="navbar-menu">
            <div class="navbar-start">
                <a class="navbar-item">
                    Home
                </a>

                <a class="navbar-item">
                    Documentation
                </a>

                <div class="navbar-item has-dropdown is-hoverable">
                    <a class="navbar-link">
                    More
                    </a>

                    <div class="navbar-dropdown">
                        <a class="navbar-item">
                            About
                        </a>
                        <a class="navbar-item">
                            Jobs
                        </a>
                        <a class="navbar-item">
                            Contact
                        </a>
                        <hr class="navbar-divider">
                        <a class="navbar-item">
                            Report an issue
                        </a>
                    </div>
                </div>
            </div>

            <div class="navbar-end">
                <div class="navbar-item" v-if="!authenticated">
                    <div class="buttons">
                    <nuxt-link :to="{ name: 'auth-signup' }" class="button is-primary">
                        <strong>Sign up</strong>
                    </nuxt-link>
                    <nuxt-link :to="{ name: 'auth-signin' }" class="button is-light">
                        Log in
                    </nuxt-link>
                    </div>
                </div>
                <div v-if="authenticated" class="navbar-item has-dropdown is-hoverable">
                    <a href="" class="navbar-link">{{ user.name }}</a>
                    <div class="navbar-dropdown is-right">
                        <a @click.prevent="logout" class="navbar-item">Logout</a>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    methods: {
        logout() {
            this.$auth.logout();
        }
    },
}
</script>

<style>

</style>
