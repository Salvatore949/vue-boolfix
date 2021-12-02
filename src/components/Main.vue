<template>
  <div>
    <header>
        <h1>BOOLFLIX</h1>
        <input type="text" id="choose" placeholder="HarryPotter">
    </header>
    <div>
    <Cards
    v-for="film in results"
    :key="film.id"
    :details="film"
    />      
    </div>
  </div>  
</template>

<script>
import axios from "axios";
import Cards from '@/components/Cards.vue'

export default {
  name: 'Main',
  components:{
    Cards
  },
  data(){
    return{
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=c53a2a603471b7e3608f9dee04a90392&query=harry+potter",
      "page": 1,
      "results": [],
      "total_pages": 2,
      "total_results": 25
      }
    },
    created(){
      this.getCharacters();
    },
    methods: {
      getCharacters(){
      axios
      .get(this.apiUrl)
      .then((result)=>{
        this.results = result.data;
      })
      }
    }
  }
</script>

<style>
  header{
      background-color: black;
      color: red;
      display: flex;
      justify-content: space-between;
      height: 8vh;
    }

    header h1{
        font-size:25px;
        padding-left: 50px;
    }

    #choose{
        height: 30px;
        display: flex;
        margin-top: 10px;
        margin-right:50px ;
    }
</style>