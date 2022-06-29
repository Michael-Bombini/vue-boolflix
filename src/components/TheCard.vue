<template>
  <div>
    <div class="card">
      <img
        class="card-img-top"
        :alt="`Immagine del film ${card.title}`"
        :src="poster"
        @error="cambiaImgError"
      />
      <div class="card-body">
        <h3 class="card-title" v-if="card.title!==undefined">{{ card.title }}</h3>
        <h3 class="card-title" v-else>{{card.name}}</h3>
        <h6 class="card-title" v-if="card.original_title!==undefined">{{ card.original_title }}</h6>
        <h6 class="card-title" v-else>{{ card.original_name}}</h6>
        <lang-flag :iso="card.original_language " />
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
  data(){
    return{
      poster : `https://image.tmdb.org/t/p/original/${this.card.poster_path}`,
    }
  },
  methods: {
    printVoto(voto) {
      return Math.round(voto / 2);
    },
    cambiaImgError(){
      this.poster = `https://d32qys9a6wm9no.cloudfront.net/images/movies/poster/500x735.png`;
    }
  },
};
</script>

<style lang="scss" scoped>
.card-body {display: none;}
.card {


  img{
    max-height: 400px;
  }

}


.card:hover .card-body{
display: block;
position: absolute;
background: rgba(0,0,0,0.7);
color: #fff;
top: 0;
left: 0;
right: 0;
bottom: 0;
}


img.star {
  width: 32px;
}
</style>
