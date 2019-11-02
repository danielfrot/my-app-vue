<template>
    <div>
        <v-row justify="center">
            <v-col cols="12">
                <v-text-field
                    v-model="textSearch"
                    label="Pesquise algo..."
                    @input="doSearch"
                ></v-text-field>
            </v-col>
           
        </v-row>

        <v-row justify="center" v-if="!textSearch">
            <v-col cols="12" md="4" class="text-center">
                <p class="overline">Digite algo para iniciar a pesquisa</p>
            </v-col>
        </v-row>

            <loading :condition="searchOnGoing">
                <v-row>
                    <v-col cols="12" md="3" lg="2" v-for="(book, i) in bookList" :key="i">
                       <book-item :book="book" />
                    </v-col>
                </v-row>
            </loading>
    </div>
</template>

<script>
    import Loading from '../loading/Loading.vue';
    import BookItem from './BookItem.vue';

    const axios = require('axios');
    
    export default {
        name: 'bookList',
        components: { Loading, BookItem },
        data(){
            return {
                textSearch: '',
                bookList: [],
                searchOnGoing: false,
            };
        },
        
        methods: {
            doSearch() {
                if(this.textSearch){
                    this.searchOnGoing = true;
                    axios.get(`https://www.googleapis.com/books/v1/volumes?q=${this.textSearch}`).then((response) => {
                        this.bookList = response.data.items;
                        this.searchOnGoing = false;
                    });
                } else{
                    this.bookList = [];
                }
            },
        },



    }
</script>

<style>

</style>