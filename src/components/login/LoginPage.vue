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
        
       <feedback/>

    </v-container>
</template>

<script>

    import Feedback from '../feedback/Feedback.vue';

export default {
        //AIzaSyD7pw_3NCFH7OxYI6OQTuGm8V0wv-lE4KU
    name: 'LoginPage',
    components: { Feedback },
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
                this.$store.commit('showErrorMessege', 'Você deve obrigatoriamente informar um token.');
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

