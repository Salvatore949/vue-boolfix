<template>
    <div id="film_list">
      <div id="description">
        <h2>{{details.original_title}}</h2>
        <p>{{details.title}}</p>
        <p>
          <i v-for="star,i of stars" :key="i" class="fas fa-star"></i>
          <i v-for="star,i of empty" :key="i" class="far fa-star"></i>
          {{details.vote_average}}</p>
        <p id="overview">{{details.overview}}</p>
        <img id="flag" :src="flagsLanguage" :alt="'bandiera' + details.original_language">
      </div>
      <img id="back_image" :src="background"  alt="background">
      
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
      details: Object,
  },
  computed:{
    flagsLanguage(){
      return require('@/assets/' + this.details.original_language +".png");
  },
  background(){
    if( this.details.backdrop_path == null){
      return require("@/assets/logo.png");
    }else{
      return "https://image.tmdb.org/t/p/w1280"+this.details.backdrop_path
    }
  },

  stars(){
    // stelle 4.1 arrotondare per eccesso, rapportarlo a 5 
    let stelle = Math.ceil(this.details.vote_average / 2);
    // let stelle = Math.floor(this.details.vote_average / 2) + 1;
    // if(stelle === 1){
    //   return 0
    // }
    return stelle;

  },

  empty(){
    
     return 5 - this.stars;
  }
  
  }
}
</script>

<style>

#back{
  background-color: gray;
}

#film_list{
  border:2px solid rgb(255, 255, 255);
  max-height:400px;
  width: 20%;
  margin:50px 60px 50px 30px;
  position: relative;
  object-fit: cover;
}

#description{
  line-height: 15px;
  padding: 0 20px;
  position: absolute;
  color: rgb(0, 0, 0);
  line-height:20px;
  color: rgb(0, 0, 0);
  text-overflow: ellipsis; 
  margin-top:15px;
}


#film_list > #back_image{
  width: 100%;
  background-size: cover;
   background-attachment: fixed;

width: 100%;
height: 100%;
}

#flag{
    width: 40px;
    margin-top:5px;
}
</style>