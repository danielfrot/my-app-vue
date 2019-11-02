<template>
    <v-container fluid>
        <v-row justify="center">
            <v-col cols="12" md="4" lg="3" class="text-center">
                <h6 class="display-2 text-uppercase">Login</h6>
                <v-text-field label="Token" v-model="token"/>
                <v-btn depressed color="green" dark block @click="login" class="mb-2">Login</v-btn>
                <v-btn text @click="loginAsGuest">Entrar como visitante</v-btn>
            </v-col>
        </v-row>

    </v-container>
</template>

<script>

    

export default {
        //AIzaSyD7pw_3NCFH7OxYI6OQTuGm8V0wv-lE4KU
    name: 'LoginPage',
    
    data() {
        return {
            token: '',
            
        };
    },
    methods: {
        login() {
            if (this.token) {
                this.$store.commit('setAuthToken', this.token);
                this.$router.push('/book');
            } else{
                this.$store.commit('showErrorMessage', 'Você deve informar um token.');
            }
            //alert(this.$store.state.authToken);
        },
        loginAsGuest() {
            this.$router.push('/book'); // TODO melhorar mais tarde

        },

    },
}
</script>

<style scoped>

</style>

