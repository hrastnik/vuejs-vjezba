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
      <button @click="sayHi">Click me to say HI!</button>
    </div>

    <p>I want my box to be:</p>
    <Label>
      Red
      <input type="radio" name="boxColor" v-model="boxColor" value="red">
    </Label>
    <Label>
      Green
      <input type="radio" name="boxColor" v-model="boxColor" value="green">
    </Label>
    <Label>
      Blue
      <input type="radio" name="boxColor" v-model="boxColor" value="blue">
    </Label>

    <div class="box" :style="{'background-color' : boxColor}"></div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      age: undefined,
      guests: ["Ivan", "Marko", "Mario", "Ivana"],
      boxColor: "red"
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
  },
  methods: {
    sayHi() {
      alert("Hi " + this.fullName);
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 1000px;
  padding: 2ch;
}
.box {
  height: 200px;
  width: 200px;
  border: 1px solid black;
  margin-top: 15px;
}
</style>
