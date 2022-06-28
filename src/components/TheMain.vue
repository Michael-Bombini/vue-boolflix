<template>
    <div>
        <div class="container">
            <div class="row g-4" v-if="!getSearched">
                <div class="col-3"  v-for="(movie,i) in getMoviesList" :key="i"><TheCard :card="movie"/></div>
            </div>
            <div v-else-if="getSearched && getMoviesList.length===0">Non è stato trovato nessun risultato</div>
        </div>
    </div>
</template>

<script>
import { state } from '../store'
import TheCard from './TheCard.vue';
    export default {
    name: "TheMain",
    computed: {
        getMoviesList() {
            return state.movies;
        },
        getSearched() {
            return state.errore;
        }
    },
    components: { TheCard }
}
</script>

<style lang="scss" scoped>

</style>