<template>
  <div>
    <div class="container">
      <div
        class="row g-4"
        v-if="getMoviesList.length > 0 && getMoviesList !== undefined"
      >
        <h1>Film</h1>
        <div class="col-3" v-for="(movie, i) in getMoviesList" :key="i">
          <TheCard :card="movie" />
        </div>
      </div>
      <div
        class="row g-4 m-3"
        v-if="getSeriesList.length > 0 && getSeriesList !== undefined"
      >
        <h1 class="py-2">Serie</h1>
        <div class="col-3" v-for="(serie, i) in getSeriesList" :key="i">
          <TheCard :card="serie" />
        </div>
      </div>
      <div v-else-if="!getFirstSearch" >Non è stato trovato nessun risultato</div>
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
