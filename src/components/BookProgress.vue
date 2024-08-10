<script setup>
import { computed } from 'vue';
    
    const props = defineProps(['books'])
    const booksRead = computed (() => {
        return props.books.filter(book => book.isRead).length
    })
    const booksReadMenssage = computed (() => {
        return booksRead.value >= props.books.length ?
        'Parabéns, você leu todos os livros' :
        `${booksRead.value} de ${props.books.length} livros lidos`
    })

</script>

<template>
    <div class="books-read">
        <label for="proggress">Seu progresso</label> <br>
        <progress :value="booksRead" :max="books.length"></progress>
        <p>{{booksReadMenssage}}</p>
    </div>
</template>