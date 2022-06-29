<template>
  <div>
    <div class="container">
      <div
        class="row g-4"
        v-if="getMoviesList.length > 0 && getMoviesList !== undefined"
      >
        <h1 class="text-light">Film</h1>
        <div class="col-sm-6 col-md-4 col-lg-3" v-for="(movie, i) in getMoviesList" :key="i">
          <TheCard :card="movie" />
        </div>
      </div>
    </div>
    <div class="container">
      <div
        class="row g-4"
        v-if="getSeriesList.length > 0 && getSeriesList !== undefined"
      >
        <h1 class="text-light">Serie</h1>
        <div class="col-sm-6 col-md-4 col-lg-3" v-for="(serie, i) in getSeriesList" :key="i">
          <TheCard :card="serie" />
        </div>
      </div>

      <div v-else-if="!getFirstSearch && (getMoviesList.length===0 && getSeriesList.length===0)" class="text-light display-6">
        Non è stato trovato nessun risultato
      </div>
    </div>
  </div>
</template>

<script>
import { state } from "../store";
import TheCard from "./TheCard.vue";
export default {
  name: "TheMain",
  computed: {
    getMoviesList() {
      return state.movies;
    },
    getSeriesList() {
      return state.series;
    },
    getFirstSearch() {
      return state.firstSearch;
    },
  },
  components: { TheCard },
};
</script>

<style lang="scss" scoped></style>
