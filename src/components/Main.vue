<template>
  <header>
      <h1>BOOLFLIX</h1>
      <input type="text" id="choose" placeholder="HarryPotter">
  </header>
</template>

<script>
export default {
  name: 'Main',
}
data(){
    return
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