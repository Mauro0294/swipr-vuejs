<template>
    <h1>Gif's</h1>
    <div class="flex justify-center">
      <a href="favorieten" class="link">Zie hier je favorieten!</a>
    </div>
    <FetchedImage />
    <MobileNav />
  </template>
  
  <script>
  import FetchedImage from './components/FetchedImage.vue'
  import MobileNav from './components/MobileNav.vue'
  
  export default {
    name: 'App',
    components: {
      FetchedImage,
      MobileNav,
    }
  }
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  
  .link {
    display: none;
  }
  
  @media screen and (min-width: 1024px) {
    .link {
      display: block;
    }
  }
  </style>