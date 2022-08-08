<template>
  <div class="app">
    <Navbar />
    <div class="presentation-container">
      <div class="presentation-img-container">
        <img class="presentation-img" src="https://m.media-amazon.com/images/I/71BPuv+iRbL._AC_SY741_.jpg" alt="presentation-img"/>
      </div>
      <div class="presentation-title-container">
        <h1 class="presentation-title">Welcome to the IMDB movies searcher</h1>
        <span>Go to the movies entry to search for a movie</span>
      </div>
    </div>

    <div class="footer bg-dark py-2 text-center">
      <span>Developed with love by Alejandro</span>
    </div>

  </div>
</template>

<script>

import Navbar from '~/components/Navbar.vue';

export default {
  name: 'IndexPage',
  components:{
    Navbar,
}
}
</script>

<style>
  body{
    background-color: #293462;
    color: white;
  }

  .presentation-container{
    padding: 30px;
    height: 90vh;
    display: flex;
  }

  .presentation-img-container{
    flex: 1;
    display: flex;
    justify-content: center;
  }

  .presentation-img{
    height: 100%;
    border-radius: 20px;
  }

  .presentation-title-container{
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: start;
  }
</style>
