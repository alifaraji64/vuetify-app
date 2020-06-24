<template>
  <div class="home">
    <h1 class="subtitle-1 grey--text">dashboard</h1>
    <v-container class="my-5">
      <!-- PLACE FOR SORTING BUTTONS START-->
      <v-row wrap>
        <v-col cols="12" xs="12" sm="3">
          <v-tooltip top>
            <template v-slot:activator="{ on }">
              <v-btn
                block
                outlined
                color="deep-purple accent-4"
                @click="sortBy('title')"
                :loading="titleLoading"
                v-on="on"
              >
                <v-icon left small>mdi-folder</v-icon>
                <span>by project name</span>
              </v-btn>
            </template>
            <span>Sort By Project Name</span>
          </v-tooltip>
        </v-col>

        <v-spacer></v-spacer>
        <v-col cols="12" xs="12" sm="4">
          <v-tooltip top>
            <template v-slot:activator="{ on }">
              <v-btn
                block
                outlined
                color="deep-purple accent-4"
                @click="sortBy('person')"
                :loading="personLoading"
                v-on="on"
              >
                <v-icon left small>mdi-account-circle</v-icon>
                <span>by person name</span>
              </v-btn>
            </template>
            <span>Sort By Person Name</span>
          </v-tooltip>
        </v-col>
      </v-row>
      <!-- PLACE FOR SORTING BUTTONS END-->
      <v-card
        class="pa-2 my-4"
        :id="project.status"
        v-for="project in projects"
        :key="project.title"
      >
        <v-row>
          <v-col cols="12" xs="12" md="6">
            <div class="caption grey--text">project title</div>
            <div>{{project.title}}</div>
          </v-col>
          <v-col cols="12" xs="6" sm="4" md="2">
            <div class="caption grey--tex">Person</div>
            <div>{{project.person}}</div>
          </v-col>
          <v-col cols="12" xs="6" sm="4" md="2">
            <div class="caption grey--tex">Due by</div>
            <div>{{project.due}}</div>
          </v-col>
          <v-col cols="12" xs="6" sm="4" md="2">
            <v-chip class="white--text right" :id="`${project.status}-chip`">{{project.status}}</v-chip>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      titleLoading: false,
      personLoading: false,

      projects: [
        {
          title: "design a website",
          person: "person one",
          due: "1st jan 20220",
          status: "ongoing"
        },
        {
          title: "code the home page",
          person: "person two",
          due: "2st jan 20220",
          status: "complete"
        },
        {
          title: "make our logo",
          person: "person three",
          due: "3st jan 20220",
          status: "complete"
        },
        {
          title: "edit the video",
          person: "person four",
          due: "4st jan 20220",
          status: "overdue"
        }
      ]
    };
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
      if (prop == "title") {
        this.titleLoading = true;
        setTimeout(() => {
          this.titleLoading = false;
        }, 300);
      } else {
        this.personLoading = true;
        setTimeout(() => {
          this.personLoading = false;
        }, 300);
      }
    }
  }
};
</script>
<style>
#ongoing {
  border-left: 5px solid orange;
}
#complete {
  border-left: 5px solid skyblue;
}
#overdue {
  border-left: 5px solid tomato;
}
#ongoing-chip {
  background: orange;
}
#complete-chip {
  background: skyblue;
}
#overdue-chip {
  background-color: tomato;
}
</style>