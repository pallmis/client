<template>
    <div>
        <nav>
            <ul>
                <li> <NuxtLink to="/"> tutoriál </NuxtLink> </li>
                <li> <NuxtLink to="/recipes"> recepty </NuxtLink> </li>
            </ul>
        </nav>
        <nav v-if="showDefaultNav" class="grey">
            <ul>
                <li> <NuxtLink to="/recipes"> recepty </NuxtLink> </li>
                <li> <NuxtLink to="/recipes/login"> přihlášení </NuxtLink> </li> <!-- změnit: login pro nepřihlášené, účet pro přihlášené -->
                <li> <NuxtLink to="/recipes/register"> registrace </NuxtLink> </li> <!-- změnit: zmizet pro přihlášené -->
            </ul>
        </nav>
        <!-- obsah -->
        <main>
            <Nuxt />
        </main>
        <!-- obsah -->
        <footer>
          <p></p>
        </footer>
    </div>
</template>

<script>
export default {
  computed: {
    showDefaultNav() {
      return this.$route.path.includes("/recipes");
    },
  },
};
</script>

<style>

a.nuxt-link-active {
  font-weight: bold;
}

a.nuxt-link-exact-active {
  color: #57C8FF;
}

main {
  margin: 0 auto;
  padding: 0;
  margin-top: 0px;
  text-align: center;
  min-height: 1000px;
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
li {
  font-weight: bold;
  margin: 0 0.5rem;
  padding: 0.25rem;
  font-size: 1.2rem;
}

a,
a:visited {
  text-decoration: none;
  color: inherit;
}

a:hover {
  color: #57C8FF;
}

footer {
  background-color: #BDBDBD;
  min-height: 50px;
  text-align: center;
}

.grey {
  background-color: #BDBDBD;
}
</style>