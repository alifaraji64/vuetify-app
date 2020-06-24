<template>
  <div class="main">
    <h1 class="subtitle-1 grey--text">team</h1>
    <v-container class="my-5">
      <v-row>
        <v-col cols="12" xs="12" sm="6" md="4" v-for="person in team" :key="person.name">
          <v-card class="text-center">
            <v-responsive>
              <v-avatar size="90">
                <img :src="getImageUrl(person.avatar)" alt="image" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="font-weight-black black--text">{{person.name}}</div>
              <div class="subtitle-2">{{person.role}}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn outlined color="deep-purple accent-4" class="mx-auto">
                <v-icon small left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  methods: {
    getImageUrl(pic) {
      return require("../assets/" + pic);
    }
  },
  data() {
    return {
      team: [
        {
          name: "the net ninja",
          role: "web developer",
          avatar: "avatar-1.png"
        },
        {
          name: "ali",
          role: "software engineer",
          avatar: "avatar-2.png"
        },
        {
          name: "aref",
          role: "social media marketing",
          avatar: "avatar-3.png"
        },
        {
          name: "hasan",
          role: "graphic designer",
          avatar: "avatar-4.png"
        },
        { name: "yadu", role: "doctor", avatar: "avatar-5.png" }
      ]
    };
  }
};
</script>

<style>
</style>