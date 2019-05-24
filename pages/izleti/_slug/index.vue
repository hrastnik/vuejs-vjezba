<template>
  <main class="container">
    <h1 v-if="izlet === undefined">Dohvaćam podatke...</h1>

    <div v-else class="trip-content">
      <h1 v-html="izlet.title.rendered"></h1>

      <div class="image-wrapper">
        <img :src="izlet.acf.featured_image" alt="Slika">
      </div>

      <p>{{izlet.acf.description}}</p>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      izlet: undefined
    };
  },
  mounted() {
    this.$axios(
      "https://education.lloyds-design.hr/wp-json/wp/v2/trips/?slug=" +
        this.$route.params.slug
    ).then(data => {
      this.izlet = data.data[0];
    });
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.trip-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1000px;
}

.image-wrapper {
  /* Ovime osiguravamo da je aspect-ratio slike 1:2 */
  position: relative;
  width: 100%;
  padding-bottom: 50%;
}

img {
  max-height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  object-fit: cover;
}

p {
  padding: 2ch;
}
</style>
