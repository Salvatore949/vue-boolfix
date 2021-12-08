<template>
  <div>
    <header>
        <h1>BOOLFLIX</h1>
        <div>
          <input type="text" id="choose" placeholder="Insert" v-model.trim="searchText">
          <button id="botton" @click.prevent="searching">Search</button>
        </div>
    </header>
    <div id="back">
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
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=c53a2a603471b7e3608f9dee04a90392&query=",
      apiUrlserie:"https://api.themoviedb.org/3/search/tv?api_key=c53a2a603471b7e3608f9dee04a90392&language=it_IT&query=",
      results: [],
      serie: [],
      searchText:"",
    }
  },
  methods: {
    getMovies(){
      axios
      .get(this.apiUrl+this.searchText)
      .then((result) => {
        this.results = result.data.results;
      })
    },
    getSeries(){
      axios
      .get(this.apiUrlserie+this.searchText)
      .then((result) => {
        this.serie = result.data.results;
      })
    },
    searching(){
      this.getMovies();
      this.getSeries();
    }
  }

  }
</script>

<style>
*{
  margin: 0;
  padding: 0;
}

header{
  display: flex;
  justify-content: space-between;
  background-color: black;
  padding: 5px 20px;

}

h1{
  color: red;
  margin:30px 0;  
}

#choose{
  height: 30px;
  margin:30px 0;

}

#botton{
  height: 30px;
  margin-left: 20px;  
}

#back{
  background-color: rgb(71, 70, 70);
  display: flex;
  flex-wrap: wrap;
}
</style>