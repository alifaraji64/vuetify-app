<template>
  <v-dialog max-width="500">
    <template v-slot:activator="{on , attrs}">
      <v-btn outlined class="success mx-auto" v-on="on" v-bind="attrs">add new project</v-btn>
    </template>
    <v-card>
      <v-card-title>
        <h2>add a new project</h2>
      </v-card-title>
      <v-form class="px-6" v-model="valid">
        <v-text-field label="title" v-model="title" prepend-icon="mdi-folder" :rules="rules"></v-text-field>
        <v-textarea label="information" v-model="content" prepend-icon="mdi-pencil" :rules="rules"></v-textarea>
        <!-- FOR DATE PICKER -->
        <v-menu>
          <template v-slot:activator="{ on, attrs }">
            <v-text-field
              label="due date"
              v-on="on"
              v-bind="attrs"
              prepend-icon="mdi-calendar-today"
              :value="formatedDate"
              :rules="rules"
            ></v-text-field>
          </template>
          <v-date-picker v-model="due"></v-date-picker>
        </v-menu>
        <!-- FOR DATE PICKER -->

        <v-btn
          outlined
          class="mx-auto my-4 primary--text"
          @click="submit"
          :disabled="!valid"
        >add project</v-btn>
      </v-form>
    </v-card>
  </v-dialog>
</template>

<script>
import format from "date-fns/format";

export default {
  data() {
    return {
      valid: null,
      title: "",
      content: "",
      due: null,
      rules: [
        v => !!v || "title is required",
        v => v.length >= 3 || "title should have more than 3 charecters"
      ]
    };
  },
  methods: {
    submit() {
      console.log(this.title, this.content);
    }
  },
  computed: {
    formatedDate() {
      return this.due ? format(new Date(this.due), "MMMM do yyyy") : "";
    }
  }
};
</script>

<style>
</style>