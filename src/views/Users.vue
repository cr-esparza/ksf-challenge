<template>
  <div class="users">
    <!-- User form starting -->
    <v-form>
      <v-container>
        <!-- Field definition and model binding -->
        <v-row>
            <v-col cols="12" md="4">
            <v-text-field
              v-model="data.custNo"
              label="Customer number"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.firstName"
              label="First name"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.lastName"
              label="Last name"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.address.streetAddress"
              label="Street Address"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.address.zipCode"
              label="Zip Code"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.address.streetName"
              label="Street Name"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.address.city"
              label="City"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="data.address.countryCode"
              label="Country Code"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn
          color="#00a1ab"
          class="mr-4 white--text"
          @click="updatePersona"
        >
        Save
      </v-btn>
      <!-- End of field definition and model binding -->
      </v-container>
    <!-- End of form -->
    </v-form>
  </div>
</template>

<script>
// Import the axios to make the API requests
import axios from 'axios';

export default {
  // View data initialization, this avoid errors
  // the model binding needs initialized data.
  name: 'users-view',
  data() {
    return {
      title: "Users view",
      data: {
        uuid: "",
        firstName: "",
        lastName: "",
        custNo: "",
        address: {
            streetAddress: "",
            zipCode: "",
            streetName: "",
            city: "",
            countryCode: "",
        },
      },
    }
  },
  // Once the component is created makes the API GET
  // request to obtain the user data for an specific ID
  created() {
    // Token, header and URL definition
    const personaRequest = axios.create({
        baseURL: "https://persona.api.ksfmedia.fi/v1/",
        headers: { "Authorization": "OAuth " + localStorage.token}
    });

    personaRequest.get(`users/${this.$route.params.id}`)
    .then(response => {
        // Once the data from the response is available
        // the component data needs to be udpated or set.
        this.data.uuid = response.data.uuid;
        this.data.custNo = response.data.cusno;
        this.data.firstName = response.data.firstName;
        this.data.lastName = response.data.lastName;
        this.data.address.streetAddress = response.data.address.streetAddress;
        this.data.address.zipCode = response.data.address.zipCode;
        this.data.address.streetName = response.data.address.streetName;
        this.data.address.city = response.data.address.city;
        this.data.address.countryCode = response.data.address.countryCode;
    }).catch(function (error) {
      // Error handling needs to be improved, stays like this due to the lack
      // of time
      alert(error);
    });
  },
  // Defining Users component methods.
  methods: {
    // Makes the API PATCH request to KSP Persona user endpoint
    // Updates User
    updatePersona () {
      // Token, header and URL definition
      const updatePersonaRequest = axios.create({
        baseURL: "https://persona.api.ksfmedia.fi/v1/",
        headers: { "Authorization": "OAuth " + localStorage.token}
      });

      // PATCH request to update only the user address as defined in the API
      updatePersonaRequest.patch(`users/${this.$route.params.id}`, {
        address: {
            countryCode: this.data.address.countryCode,
            zipCode: this.data.address.zipCode,
            streetAddress: this.data.address.streetAddress,
        }
      }
    ).then(response => {
        alert('sucess');
        // Component data updated with the response data.
        this.data.address.countryCode = response.data.address.countryCode;
        this.data.address.zipCode = response.data.address.zipCode;
        this.data.address.streetAddress = response.data.address.streetAddress;
    }).catch(function (error) {
      // Error handling needs to be improved, stays like this due to the lack
      // of time
      alert(error);
    });
   },
  }
}
</script>