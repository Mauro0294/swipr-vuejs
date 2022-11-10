<template>
  <div class="wrapper">
    <img class="giphyImage" src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Loading_icon.gif?20151024034921" alt="Gif">
    <p id="gifDescription"></p>
    <div class="button_wrapper">
      <button @click="like()"><img src="../assets/like_heart.svg" class="like" alt="like icon"></button>
      <button @click="dislike()"><img src="../assets/dislike.png" class="dislike" alt="dislike icon"></button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FetchedImage',
    data() {
      return {
        randomGif: [],
        gifId: 0,
        imageContainer: [],
        gifDescription: '',
      }
    },
    methods: {
      async fetchData() {
        await fetch("https://api.giphy.com/v1/gifs/random?api_key=fEMFWtdn7bqvfjkwkiwH1O87iPZ27yPg&tag=&rating=g")
            .then(response => response.json())
            .then(data => {
              this.randomGif = data.data.images.downsized_medium.url;
              this.gifId = data.data.id;
              this.gifDescription = data.data.title;
            })
            .catch(error => console.log(error));
            document.querySelector(".giphyImage").src = this.randomGif;
        },
      like() {
        if (localStorage.getItem("favorietenGifs") === null) {
            localStorage.setItem("favorietenGifs", JSON.stringify([]));
        }

        const oudeFavorieten = JSON.parse(localStorage.getItem('favorietenGifs'));
        const nieuweFavoriet = this.gifId;

        oudeFavorieten.push(nieuweFavoriet);
        localStorage.setItem('favorietenGifs', JSON.stringify(oudeFavorieten));

        this.fetchData();
      },
      dislike() {
        this.fetchData();
      }
    },
    mounted() {
      const gifDescription = document.querySelector("#gifDescription");
      this.imageContainer = document.querySelector(".giphyImage");
      this.imageContainer.addEventListener('click', () => {
            this.imageContainer.classList.toggle('scale');
            if (this.imageContainer.classList.contains('scale')) {
              gifDescription.innerText = this.gifDescription;
            } else {
              gifDescription.innerText = '';
            }
        });
      this.fetchData();
    }
}

</script>

<style scoped>
.wrapper {
  margin-top: 40px;
  width: 100%;
}

button {
  background: none;
  outline: none;
  border: none;
  cursor: pointer;
}

.scale {
    transform: scale(1.3);
}

.button_wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 28px;
}

.giphyImage {
  border: 2px solid red;
  width: 500px;
  aspect-ratio: 16/9;
  max-width: 100%;
}

.like {
  width: 40px;
}

.dislike {
  width: 56px;
}

#gifDescription {
  margin-top: 40px;
}
</style>