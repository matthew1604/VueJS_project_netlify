<template>
  <div id="form">
    <b-form @submit="onSubmit">
      <b-form-group id="input-group-1" label="Nom :" label-for="input-1">
        <b-form-input
          id="input-1"
          v-model="lastname"
          type="text"
          required
          placeholder="Entrez votre nom"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-4" label="Prenom :" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="firstname"
          type="text"
          required
          placeholder="Entrez votre prenom"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Email :" label-for="input-2">
          <b-form-input
          id="input-3"
          v-model="email"
          type="text"
          required
          placeholder="Entrez votre email"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-3" label="Mot de passe :" label-for="input-3">
         <b-form-input
          id="input-3"
          v-model="password"
          type="text"
          required
          placeholder="Entrez un mot de passe"
        ></b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary">S'inscrire</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
  export default {
    name: "Inscription",
    data() {
      return {
          email: '',
          password: '',
          firstname: '',
          lastname: ''
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        console.log(this.email, this.password, this.firstname, this.lastname)
        axios
        .post("https://projet-js-nasi-vergely.herokuapp.com/signin", {
          email: this.email,
          password: this.password,
          firstname: this.firstname,
          lastname: this.lastname
          })
        .then(response => {
          console.log(response.data)
        })
        .catch(error => console.log(error));
      }
    } 
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#form {
    margin: 5%;
}
</style>