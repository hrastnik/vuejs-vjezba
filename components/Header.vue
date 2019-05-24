<template>
  <header class="header">
    <nuxt-link to="/">Home</nuxt-link>
    <nuxt-link to="/o-nama">O nama</nuxt-link>
    <nuxt-link to="/vjezba">Vjezba</nuxt-link>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
.header {
  height: 100px;
  background: gray;
  display: flex;
  align-items: center;
}

a {
  color: white;
  font-size: 22px;
  padding: 10px;
}
</style>
