<template>
    <div>
        <nav>
            <ul>
                <li> <NuxtLink to="/"> domovská stránka </NuxtLink> </li>
                <li> <NuxtLink to="/recepty"> recepty </NuxtLink> </li>
            </ul>
        </nav>
        <main>
            <Nuxt/>
        </main>
    </div>
</template>

<style>

a.nuxt-link-active {
  font-weight: bold;
}

a.nuxt-link-exact-active {
  color: #57C8FF;
}

main {
  margin: 0 auto;
  padding: 0 1rem;
  margin-top: 100px;
  max-width: 1280px;
  text-align: center;
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
li {
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

</style>