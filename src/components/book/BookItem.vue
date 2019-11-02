<template>
    <v-card
        class="mx-auto book-card"
    >
        <v-card-text>
    
        <p class="display-1 text--primary">
            <span>{{ book.volumeInfo.title.substring(0, maxTitleLength) }}</span>
            <span v-if="book.volumeInfo.title.length > maxTitleLength">...</span>
        </p>
        <div class="text--primary">
            {{ book.volumeInfo.subtitle || 'Sem descrição' }}
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
</template>

<script>
    export default {
        name: 'BookItem',
        props: {
            book: { type: Object, required: true },
        },
        data() {
            return {
                maxTitleLength: 20,
            }
        }
    }
</script>

<style>
    .book-card {
        height: 100%;
    }
</style>