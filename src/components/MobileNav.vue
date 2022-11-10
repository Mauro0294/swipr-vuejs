<template>
  <div class="nav_wrapper">
    <div class="nav">
      <a href="/">
        <img src="../assets/home.svg" class="nav_icon" alt="home icon">
      </a>
      <a href='favorieten'>
        <img src="../assets/heart.svg" class="nav_icon" alt="heart icon">
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MobileNav',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav_wrapper {
  width: 100vw;
  display: flex;
  justify-content: center;
}

.nav {
  position: absolute;
  bottom: 12px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 64px;
  width: 80%;
  border-radius: 24px;
  box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
}

.nav_icon {
  width: 40px;
}

@media screen and (min-width: 1024px) {
  .nav {
    display: none;
  }
}

@media screen and (min-width: 768px) {
  .nav {
    height: 96px;
  }
  .nav_icon {
    width: 64px;
  }
}
</style>
