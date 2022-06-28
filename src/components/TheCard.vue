<template>
  <div>
    <div class="card">
      <img
        class="card-img-top"
        :alt="`Immagine del film ${card.title}`"
        :src="`https://image.tmdb.org/t/p/original/${card.poster_path}`"
      />
      <div class="card-body">
        <h3 class="card-title">{{ card.title }}</h3>
        <h6 class="card-title">{{ card.original_title }}</h6>
        <h6 class="card-title">Lingua : {{ card.original_language }}</h6>
        <p class="card-text">Descrizione.....</p>
        <p>Voto {{ printVoto(card.vote_average) }}</p>
        <span v-for="n in 5" :key="n">
          <img
            src="https://d1nhio0ox7pgb.cloudfront.net/_img/g_collection_png/standard/512x512/star.png"
            alt=""
            class="star"
            v-if="n <= printVoto(card.vote_average)"
          />
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Five_Pointed_Star_Solid.svg/2175px-Five_Pointed_Star_Solid.svg.png"
            class="star"
            alt=""
            v-else
          />
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheCard",
  props: {
    card: Object,
  },
  methods: {
    printVoto(voto) {
      return Math.round(voto / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  height: 100%;

  img {
    width: 50px;
  }
}

img.star {
  width: 32px;
}
</style>
