<template>
  <v-app color="red">
    <NavBar />
    <v-content class="mx-4">
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import NavBar from "@/components/NavBar";
export default {
  name: "App",

  components: { NavBar },

  data: () => ({
    //
  })
};
</script>
<style scoped>
</style>
