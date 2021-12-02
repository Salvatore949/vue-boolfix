<template>
  <div id="film_list">
    <h2>{{details.original_title}}</h2>
    <p>{{details.title}}</p>
    <p>{{details.vote_average}}</p>
    <p>{{details.original_language}}</p>
  </div>
</template>

<script>
export default {
  name:'Cards',
  props:{
      details:Object,
  }
}
</script>

<style>

</style>