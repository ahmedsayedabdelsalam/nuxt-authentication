<template>
    <div class="columns con">
        <div class="column is-half is-offset-one-quarter">
            <div class="field">
                <p class="control has-icons-left has-icons-right">
                    <input class="input" type="email" placeholder="Email" v-model="form.email" :class="{ 'is-danger': errors.email }">
                    <p class="help is-danger" v-if="errors.email">{{errors.email[0]}}</p>
                </p>
            </div>
            <div class="field">
                <p class="control has-icons-left">
                    <input class="input" type="password" placeholder="Password" v-model="form.password" :class="{ 'is-danger': errors.password }">
                    <p class="help is-danger" v-if="errors.password">{{errors.password[0]}}</p>
                </p>
            </div>
            <div class="field">
                <p class="control">
                    <button @click="submit" class="button is-success">
                        Login
                    </button>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    middleware: 'guest',
    data() {
        return {
            form: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        async submit() {
            try {
                await this.$auth.login({
                    data: this.form
                })
                this.$router.push({
                    path: this.$router.query.redirect || '/'
                })   
            } catch (error) {
                
            }
        }
    },
}
</script>

<style>

</style>
