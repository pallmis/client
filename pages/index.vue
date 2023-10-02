<template>
  <div>
    <h1> AJAX tutoriál - úvodní stránka </h1>
    <h3> odkazy </h3>
    <ul>
      <li> <NuxtLink to="/recepty"> recepty </NuxtLink> </li>
    </ul>
  </div>
</template>

<script>
export default {
  asyncData() {
    return {
      rendering: process.server ? 'server' : 'client'
    }
  }
}
</script>
