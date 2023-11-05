<template>
  <header>
    <div class="text-box">
      <h1>Ajax Tutorial</h1>
      <p class="mt-3">vytvoření webové aplikace</p>
      <nuxt-link class="btn btn-outline btn-large btn-info" to="/recipes">
        na recepty <span class="ml-2">&rarr;</span>
      </nuxt-link>
    </div>
  </header>
</template>

<script>
export default {
  head() {
    return {
      title: "Home page"
    };
  },
};
</script>

<style>
header {
  min-height: 100vh;
  background-image: linear-gradient(
      to right,
      rgba(0, 0, 0, 0.9),
      rgba(0, 0, 0, 0.4)
    ),
    url("../components/img/stul.png");
  background-position: center;
  background-size: cover;
  position: relative;
}
.text-box {
  position: absolute;
  top: 50%;
  left: 10%;
  transform: translateY(-50%);
  color: #fff;
}
.text-box h1 {
  font-family: cursive;
  font-size: 5rem;
}
.text-box p {
  font-size: 2rem;
  font-weight: lighter;
}
</style>


<!-- <template>
  <div>
    <div class="div1">
    </div>
    <h1> AJAX tutoriál </h1>
    <div>
        <img src="../components/img/nuxt_setup.png" alt="">
        <img src="../components/img/nuxt_setup2.png" alt="">
    </div>
  </div>
</template>

<style>

.div1 {
    background-color: #BDBDBD;
    min-height: 50px;
}

img {
  padding: 5px;
  max-width: 600px;
}

</style> -->