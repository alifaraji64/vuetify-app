<template>
  <div class="projects">
    <v-main>
      <v-expansion-panels class="my-4">
        <v-expansion-panel v-for="project in myProjects" :key="project.title">
          <v-expansion-panel-header>{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content>{{project.content}}</v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-main>
  </div>
</template>
<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "design a website",
          person: "person one",
          due: "1st jan 20220",
          status: "ongoing",
          content: "this is my content this is my content this is my content"
        },
        {
          title: "code the home page",
          person: "person two",
          due: "2st jan 20220",
          status: "complete",
          content: "this is my content this is my content this is my content"
        },
        {
          title: "make our logo",
          person: "person three",
          due: "3st jan 20220",
          status: "complete",
          content: "this is my content this is my content this is my content"
        },
        {
          title: "edit the video",
          person: "person four",
          due: "4st jan 20220",
          status: "overdue",
          content: "this is my content this is my content this is my content"
        }
      ]
    };
  },
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.person == "person one";
      });
    }
  }
};
</script>>
