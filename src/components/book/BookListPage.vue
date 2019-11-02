<template>
    <v-container fluid>
        <v-row justify="center">
            <v-col cols="12" md="4" lg="3" class="text-center">
                <h6 class="display-2 text-uppercase">Livros</h6>
            </v-col>
            
        </v-row>
        
        <book-list />

    </v-container>
</template>

<script>
    import BookList from "./BookList.vue";
    export default {
            //AIzaSyD7pw_3NCFH7OxYI6OQTuGm8V0wv-lE4KU
        name: 'BookListPage',
        components: { BookList },
        
    };
</script>

<style scoped>

</style>

