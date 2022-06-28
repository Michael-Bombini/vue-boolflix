<template>
    <div>
        <div class="input-group mb-3">
            <input type="text" class="form-control" placeholder="Inserisci titolo da cercare" v-model="searchedTitle">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="getSearchedTitle">Cerca!</button>
        </div>

    </div>
</template>

<script>
import { state } from '../store'
import axios from 'axios';
    export default {
        name: "TheHeader",
        data(){
            return{
                searchedTitle : "",
            }
        },


        methods : {
            getSearchedTitle(){
                state.searched = this.searchedTitle;
                console.log(state.searched);
                this.fetchSearched();  
            },

            fetchSearched() {
                axios
                .get("https://api.themoviedb.org/3/search/movie", {
                params: {
                    api_key: "049efd07b3cd401f7f0d67417708f39c",
                    query: state.searched,
                    language: "it-IT",
                },})
                .then((response) => {
                    state.movies = response.data.results;
                });
  }


        },



    }
</script>

<style lang="scss" scoped>

</style>