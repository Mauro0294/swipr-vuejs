<template>
  <h1>Favorieten gif's</h1>
  <a href="/">Terug van de home pagina</a>
  <MobileNav />
</template>
  
  <script>
  import MobileNav from './components/MobileNav.vue'

  export default {
    name: 'favorietenPage',
    components: {
      MobileNav,
    },
    data() {
      return {
        items: [],
      }
    },
    methods: {
      getFavorieten() {
        const favorieten = localStorage.getItem('favorietenGifs');
        this.items = JSON.parse(favorieten);

        for (let x = 0; x < this.items.length; x++) {
          const img = document.createElement('img');
          img.src = `https://media.giphy.com/media/${this.items[x]}/giphy.gif`;
          img.classList.add('gif')
          document.body.appendChild(img);
        }
      },
    },
    mounted() {
      this.getFavorieten();
    },
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

  .gif {  
    max-width: 100%;
  }

  @media screen and (min-width: 1024px) {
    .gif {
    width: 300px;
    height: 200px;
    max-width: 100%;
  }
  }
  </style>
  