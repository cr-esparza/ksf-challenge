<template>
<v-app>
    <!-- Start of Navigation -->
    <nav>
      <!-- Start of app toolbar -->
      <v-app-bar color="#333" class="white--text" app>
        <v-app-bar-nav-icon
          @click.stop="drawer = !drawer"
          class="hidden-md-and-up theme--dark"
        ></v-app-bar-nav-icon>
        <v-toolbar-title class="headline text-uppercase"
          >KSF Persona Challenge</v-toolbar-title
        >
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn class="white--text" text to="/about">About</v-btn>
        </v-toolbar-items>
      </v-app-bar>
      <!-- End of app toolbar -->

      <!-- Start of mobile side menu -->
      <v-navigation-drawer app v-model="drawer" right>
        <!-- Menu title -->
        <v-toolbar flat>
          <v-list>
            <v-list-item>
              <v-list-item-title class="title">Menu</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-toolbar>
        <v-divider></v-divider>
        <!-- Menu Links -->
        <v-list>
          <v-list-item to="/">
            <v-list-item-action>
              <v-icon>mdi-home</v-icon>
            </v-list-item-action>
            <v-list-item-content>Home</v-list-item-content>
          </v-list-item>
          <v-list-item to="/about">
            <v-list-item-action>
              <v-icon>description</v-icon>
            </v-list-item-action>
            <v-list-item-content>About</v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <!-- End of mobile side menu -->
    </nav>
    <!-- End of Navigation -->

    <v-content>
      <!-- Display view pages here based on route -->
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<style lang="scss">
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
  export default {
    name: "App",
    data() {
      return {
        drawer: false // Hide mobile side menu by default
      };
    },
    methods:{
      isUserAuthenticated() {
        if(localStorage.token) {
          return true;
        }
        return false;
      }
    }
  };
</script>
