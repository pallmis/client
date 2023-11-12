<template>
    <main class="container mt-5">
      <div class="row">
        <div class="col-12 text-right mb-4">
          <div class="d-flex justify-content-between">
            <h3>Recepty</h3>
            <nuxt-link to="/recipes/add" class="btn btn-info">Add Recipe</nuxt-link>
          </div>
        </div>
        <template v-for="recipe in recipes">
          <div class="col-lg-3 col-md-4 col-sm-6 mb-4"> 
            <!-- :key="recipe.id" -->
            <recipe-card :onDelete="deleteRecipe" :recipe="recipe"></recipe-card>
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
      RecipeCard
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
    methods: {
      async deleteRecipe(recipe_id) {
        try {
          await this.$axios.$delete(`/recipes/${recipe_id}/`); 
          let newRecipes = await this.$axios.$get("/recipes/"); 
          this.recipes = newRecipes; 
        } catch (e) {
          console.log(e);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  </style>