<template>
  <nav>
    <v-app-bar app color="purple darken-2">
      <v-toolbar-title class="text-uppercase">
        <span class="font-weight-light white--text">Todo</span>
        <span class="white--text">ninjas</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn color="red accent-3">
        <span class="white--text">signout</span>
        <v-icon right class="white--text">mdi-exit-to-app</v-icon>
      </v-btn>
      <v-app-bar-nav-icon color="white" @click="toggle"></v-app-bar-nav-icon>
    </v-app-bar>
    <v-navigation-drawer temporary color="purple darken-2" right v-model="drawer" app>
      <v-col cols="12" align-center>
        <v-row>
          <v-avatar size="100" class="mx-auto">
            <img src="../assets/avatar-1.png" alt="myImage" />
          </v-avatar>
        </v-row>
        <v-row justify-center>
          <p class="mx-auto white--text">the net ninja</p>
        </v-row>
        <!-- FOR POPUP -->
        <v-row class="mx-auto mt-6">
          <Popup />
        </v-row>
        <!-- FOR POPUP -->
      </v-col>
      <v-list-item v-for="(link,index) in links" :key="index" router :to="link.route">
        <v-list-item-icon>
          <v-icon class="white--text">{{link.icon}}</v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from "./Popup";
export default {
  components: {
    Popup
  },
  data() {
    return {
      drawer: false,
      links: [
        { icon: "mdi-view-dashboard", text: "DashBoard", route: "/" },
        { icon: "mdi-folder", text: "my Projects", route: "/projects" },
        { icon: "mdi-account", text: "Team", route: "/team" }
      ]
    };
  },
  methods: {
    toggle() {
      this.drawer ? (this.drawer = false) : (this.drawer = true);
    }
  }
};
</script>

<style>
</style>