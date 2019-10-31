<template>
  <v-layout align-center justify-center>
    <v-flex xs12 sm8 md4>
      <v-card class="elevation-12">
        <v-toolbar dark color="#f07e26">
          <v-toolbar-title>KSF Persona login</v-toolbar-title>
        </v-toolbar>
        <v-card-text>
        <!-- Login form start -->
          <v-form>
            <v-text-field
              v-model="data.username"
              prepend-icon="person"
              name="login"
              label="Login"
              id="login"
              type="text"
            ></v-text-field>
            <v-text-field
              v-model="data.password"
              prepend-icon="lock"
              name="password"
              label="Password"
              id="password"
              type="password"
            ></v-text-field>
          </v-form>
        <!-- Login form ends -->
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <!-- Defining login button and binding method -->
          <v-btn
            @click="loginPersona"
            dark color="#00a1ab">Login</v-btn>
          <!-- End of button definition -->
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
// Import library to make API request
import axios from 'axios';
// Import router to make a redirection to other view
import router from '../router'

export default {
  // Component data initialization. Models binding data needs to be
  // initialized
  name: 'login-view',
  data() {
    return {
      title: "Login view",
      data: {
        username: "",
        password: "",
      },
    }
  },
  // Defining loging component methods.
  methods: {
    // Makes the API request to KSP Persona login endpoint
    // To get Authentication token.
    loginPersona () {
      axios.post("https://persona.api.ksfmedia.fi/v1/login", {
        username: this.data.username,
        password: this.data.password,
      }
    ).then(response => {
      // Save token in localStorage
      localStorage.token = response.data.token;

      // Redirect to the users view for the user with uuid logged in
      router.push({ path: `/users/${response.data.uuid}`});
    });
   },
  }
}
</script>
