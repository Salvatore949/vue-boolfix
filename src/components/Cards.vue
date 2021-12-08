<template>
    <div id="film_list">
      <h2>{{details.original_title}}</h2>
      <p>{{details.title}}</p>
      <p>{{details.vote_average}}</p>
      <p>{{details.overview}}</p>
      <img :src="flagsLanguage" :alt="'bandiera' + details.original_language">
      <img :src="background" alt="background">
    </div>
</template>

<script>
export default {
  name:'Cards',
  data: () => ({
    "backdrop_sizes": [
      "w300",
      "w780",
      "w1280",
      "original"
    ],
    "logo_sizes": [
      "w45",
      "w92",
      "w154",
      "w185",
      "w300",
      "w500",
      "original"
    ],
    "poster_sizes": [
      "w92",
      "w154",
      "w185",
      "w342",
      "w500",
      "w780",
      "original"
    ],
    "profile_sizes": [
      "w45",
      "w185",
      "h632",
      "original"
    ],
    "still_sizes": [
      "w92",
      "w185",
      "w300",
      "original"
    ]
  }),
  props:{
      details:Object,
  },
  computed:{
    flagsLanguage(){
      return require('@/assets/' + this.details.original_language +".png");
  },
  background(){
    if( this.details.backdrop_path == null){
      return require("@/assets/logo.png");
    }else{
      return "https://image.tmdb.org/t/p/w780"+this.details.backdrop_path
    }
  }


  
  }
}
</script>

<style>

#back{
  background-color: gray;
}

 #film_list{
   background-color: yellow;
   border:2px solid rgb(255, 255, 255);
   height:60vh;
   width: 20%;
   margin:50px 60px 50px 30px;
 }

 #film_list > img{
   width:50px;
 }

</style>