<template>
    <div>
        <ul>
            <li  v-for="(movie,i) in getMoviesList" :key="i">{{movie}}</li>
        </ul>

    </div>
</template>

<script>
import { state } from '../store'
    export default {
        name : "TheMain",
        computed : {
            getMoviesList() {
                return state.movies;
            }
        }

    }
</script>

<style lang="scss" scoped>

</style>