<template>
    <main class="container mt-5">
      <div class="row">
        <div class="col-12 text-right mb-4">
          <div class="d-flex justify-content-between">
            <h3>Recepty</h3>
            <nuxt-link to="/recipes/add" class="btn btn-info">přidat recept</nuxt-link>
          </div>
        </div>
        <template v-for="recipe in recipes">
          <div class="col-lg-3 col-md-4 col-sm-6 mb-4"> 
            <!-- :onDelete="deleteRecipe" -->
            <recipe-card :key="recipe.id" :recipe="recipe"></recipe-card>
          </div>
        </template>
      </div>
    </main>
  </template>

  <script>
  import RecipeCard from "~/components/RecipeCard.vue";
  
  export default {
    head() {
      return {
        title: "seznam receptů"
      };
    },
    components: {
      RecipeCard,
    },
    async asyncData({ $axios, params }) {
      try {
        let recipes = await $axios.$get(`/recipes/`);
        console.log(recipes);
        return { recipes };
      } catch (e) {
        return { recipes: [] };
      }
    },
    data() {
      return {
        recipes: []
      };
    },
  };
  </script>

  <style scoped>
  a,
  a:visited {
  text-decoration: none;
  color: none;
  }
  </style>