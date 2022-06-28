<template>
    <div>
        <div class="container">
            <div class="row g-4" v-if="getMoviesList.length>0 && getMoviesList!==undefined">
                <div class="col-3"  v-for="(movie,i) in getMoviesList" :key="i"><TheCard :card="movie"/></div>
            </div>
            <div v-else>Non è stato trovato nessun risultato</div>
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
       
    },
    components: { TheCard }
}
</script>

<style lang="scss" scoped>

</style>