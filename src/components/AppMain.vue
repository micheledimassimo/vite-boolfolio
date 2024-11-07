<script>
import axios from 'axios';

export default {
  data() {
    return { 
      projects: []
    }
    
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects() {
      axios
          .get('http://127.0.0.1:8000/api/projects')
          .then((res) => {
            this.projects = res.data.data.projects;
            console.log(this.projects);
          });
    }
}
}
</script>

<template>
  <div class="container">
    <div class="projects-container row">
      <div v-for="project in projects" :key="project.id" class="col-3">
        <h3>
          {{ project.name }}
        </h3>
        <h5>
          {{ project.company }}
        </h5>
        <p>
          {{ project.workers }}
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;

.col-3 {
  border: 1px solid blue;
  text-align: center;
  h3 {
    margin-bottom: 20px;
    margin-top: 10px;
  }
}
</style>
