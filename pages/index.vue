<template>
  <main class="container">
    <h1>Izleti</h1>

    <!-- 
      Sa v-for direktivom obilazimo svaki izlet u listi
      Za svaki izlet prikazujemo link na detalje o tom
      izletu.

      Koristimo v-html direktivu kako bi se pravilno 
      prikazivali hrvatski znakovi (č, ć, đ...)
    -->
    <nuxt-link
      v-for="(izlet, i) in izleti"
      :key="i"
      :to="'/izleti/' + izlet.slug"
      v-html="izlet.title.rendered"
    ></nuxt-link>
  </main>
</template>

<script>
export default {
  data() {
    return {
      izleti: []
    };
  },
  created() {
    this.$axios("https://education.lloyds-design.hr/wp-json/wp/v2/trips").then(
      data => {
        this.izleti = data.data;
      }
    );
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  font-size: 25px;
}

a {
  font-size: 18px;
  padding: 10px;
}
</style>
