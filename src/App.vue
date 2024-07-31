<script>
import axios from "axios";
import Project from "./components/ProjectComponent.vue";

export default {
  name: "Projects",
  components: {
    Project,
  },
  data() {
    return {
      title: "Projects",
      projects: [],
    };
  },
  methods: {
    testLifeCycle() {
      console.log("prova ciclo vita Vue");
    },
    getProjects() {
      const result = axios
        .get("http://127.0.0.1:8000/api/projects")
        .then((response) => {
          console.log(response);
          console.log("fin qui tutto bene");
          console.log(response.data.results);

          this.projects = response.data.results;
        })
        .catch((error) => console.log(error));
    },
  },
  created() {
    this.testLifeCycle();
    this.getProjects();
  },
};
</script>

<template>
  <header>header</header>
  <main>
    <div class="container">
      <h1>{{ title }}</h1>
      <div class="row">
        <div class="col-3" v-for="project in projects">
          <Project
            :title="project.title"
            
          />
        </div>
      </div>
    </div>
  </main>
  <footer>footer</footer>
</template>

<style lang="scss" scoped></style>
