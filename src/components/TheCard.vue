<template>
  <div>
    <div class="card" @mouseover.once="fetchCast">
      <img v-if="card.poster_path!==null"
        class="card-img-top"
        alt="Immagine del film"
        :src="`https://image.tmdb.org/t/p/original/${card.poster_path}`"
      />
      <img v-if="card.poster_path===null" src="https://d32qys9a6wm9no.cloudfront.net/images/movies/poster/500x735.png" alt="">
      <div class="card-body">
        <h3 class="card-title" v-if="card.title!==undefined">{{ card.title }}</h3>
        <h3 class="card-title" v-else>{{card.name}}</h3>
        <h6 class="card-title" v-if="card.original_title!==undefined">{{ card.original_title }}</h6>
        <h6 class="card-title" v-else>{{ card.original_name}}</h6>
        <lang-flag class="py-3" :iso="card.original_language " />
        <div>

 
        <span v-for="n in 5" :key="n">
          <img
            src="https://d1nhio0ox7pgb.cloudfront.net/_img/g_collection_png/standard/512x512/star.png"
            alt=""
            class="star"
            v-if="n <= printVoto(card.vote_average)"
          />
          <img
            src="https://simg.nicepng.com/png/small/1-16904_star-star-white-five-pointed-star.png"
            class="star"
            alt=""
            v-else
          />
        </span>
        </div>
        <p class="card-text py-4">{{card.overview}}</p>


          <!-- <div  v-if="cast">

            <p class="text-light">{{cast[0].character}}</p>
          <img :src="`https://image.tmdb.org/t/p/original/${cast[0].profile_path}`" alt="" class="cast-icon">
             <p class="text-light">{{cast[0].character}}</p>
          </div> -->

      </div>
    </div>
  </div>
</template>

<script>
// import axios from 'axios';

export default {
  name: "TheCard",
  data(){
    return{
      cast : [{}],
    }
  },
  props: {
    card: Object,
  },
  methods: {
    printVoto(voto) {
      return Math.round(voto / 2);
    },
    // fetchCast(){
    //   const idHover = this.card.id;
    //      axios
    //       .get(`https://api.themoviedb.org/3/movie/${idHover}/credits`, {
    //         params: {
    //           api_key: "049efd07b3cd401f7f0d67417708f39c",
    //         },
    //       })
    //       .then((response) => {
    //         this.cast = response.data.cast;
    //       });
    // }
  },

};
</script>

<style lang="scss" scoped>
.card-body {display: none; overflow: auto;}
.card {


height: 390px;
img:not(.cast-icon) {
  height: 100%;
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
  height: 32px;
}

.cast-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;

}
</style>
