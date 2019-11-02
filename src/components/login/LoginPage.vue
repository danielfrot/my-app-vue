<template>
    <v-container fluid>
        <v-row justify="center">
            <v-col cols="12" md="4" lg="3" class="text-center">
                <h6 class="display-2 text-uppercase">Login</h6>
                <v-text-field label="Token" v-model="token"/>
                <v-btn depressed color="primary" dark block @click="login" class="mb-2">Login</v-btn>
                <v-btn text color="secondary" @click="loginAsGuest">Entrar como visitante</v-btn>
            </v-col>
        </v-row>

    </v-container>
</template>

<script>

    

export default {
    name: 'LoginPage',
    
    data() {
        return {
            token: 'AIzaSyD7pw_3NCFH7OxYI6OQTuGm8V0wv-lE4KU',
            
        };
    },
    methods: {
        login() {
            if (this.token) {
                this.$store.commit('setAuthToken', this.token);
                this.$store.commit('setLogged', true);
                this.$router.push('/book');
            } else{
                this.$store.commit('showErrorMessage', 'Você deve informar um token.');
            }
            //alert(this.$store.state.authToken);
        },
        loginAsGuest() {
            this.$store.commit('setLogged', true);
            this.$router.push('/book'); // TODO melhorar mais tarde

        },

    },
}
</script>

<style scoped>

</style>

