<template>
  <section class="container">
    <span>First name:</span>
    <input type="text" v-model="firstName" placeholder="First Name">

    <br>

    <span>Last name:</span>
    <input type="text" v-model="lastName" placeholder="Last Name">

    <br>

    <span>Age:</span>
    <input type="number" v-model.number="age">

    <div v-if="fullName.length >= 2">
      <h2>Hello {{fullName}}</h2>

      <p v-if="age < 20">{{fullName}} ima manje od 20 godina</p>
      <p v-else>{{fullName}} ima 20 ili vise godina</p>

      <h3>Gosti:</h3>
      <ul>
        <li v-for="guest in guests" :key="guest">{{guest}}</li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      age: undefined,
      guests: ["Ivan", "Marko", "Mario", "Ivana"]
    };
  },
  computed: {
    fullName() {
      return this.firstName + " " + this.lastName;
    }
  },
  watch: {
    fullName(newName) {
      console.log("Full name changed to", newName);
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 1000px;
  padding: 2ch;
}
</style>
