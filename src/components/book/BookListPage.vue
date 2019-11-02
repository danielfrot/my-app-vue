<template>
    <v-container fluid>
        <v-row justify="center">
            <v-col cols="12" md="4" lg="3" class="text-center">
                <h6 class="display-2 text-uppercase">Livros</h6>
            </v-col>
        </v-row>
        <v-row justify="center">
            <v-col cols="12" md="3" lg="2" v-for="(book, i) in bookList" :key="i">
                    <v-card
                        class="mx-auto"
                    >
                        <v-card-text>
                       
                        <p class="display-1 text--primary">
                            {{ book.volumeInfo.title }}
                        </p>
                        <div class="text--primary">
                            {{ book.volumeInfo.subtitle }}
                        </div>
                        </v-card-text>
                        <v-card-actions>
                        <v-btn
                            text
                            small
                            color="primary"
                        >
                            Ver Detalhes
                        </v-btn>
                        </v-card-actions>
                    </v-card>
            </v-col>
        </v-row>
        
    </v-container>
</template>

<script>
    const axios = require('axios');
    export default {
            //AIzaSyD7pw_3NCFH7OxYI6OQTuGm8V0wv-lE4KU
        name: 'BookListPage',
        data(){
            return {
                bookList: [
                    { title: 'Livro 1', desc: 'Descrição qualquer...' },
                    { title: 'Livro 2', desc: 'Descrição qualquer...' },
                    { title: 'Livro 3', desc: 'Descrição qualquer...' },
                    { title: 'Livro 4', desc: 'Descrição qualquer...' },
                    { title: 'Livro 5', desc: 'Descrição qualquer...' },
                    { title: 'Livro 6', desc: 'Descrição qualquer...' },
                    { title: 'Livro 7', desc: 'Descrição qualquer...' },
                    { title: 'Livro 8', desc: 'Descrição qualquer...' },
                    { title: 'Livro 9', desc: 'Descrição qualquer...' },
                    { title: 'Livro 10', desc: 'Descrição qualquer...' },
                ],
            };
        },
        created() {
            axios.get('https://www.googleapis.com/books/v1/volumes?q=flowers').then((response) => {
                this.bookList = response.data.items;
            });
        },
        
    };
</script>

<style scoped>

</style>

