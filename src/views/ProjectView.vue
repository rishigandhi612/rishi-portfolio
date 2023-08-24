<template>
  <v-main class="pa-0 ma-0">
    <v-container class="my-3">
      <!-- Header Row -->
      <v-row>
        <v-col cols="12">
          <h1>My Projects</h1>
          <p>Currently I don't have much experience, but I'm giving my best to learn and grow.</p>
        </v-col>
      </v-row>
      <!-- Header Row -->
      <!-- Cards Row -->
      <v-row>
        <v-col v-for="project in projects" :key="project.title" cols="12" md="4">
          <v-card  class="pa-5" style="display: flex;flex-direction: column;justify-content: space-between; background-color: white; border-radius: 15px; border: 0;"
            elevation="0" outlined>
            
            <p style="font-size: 120%; font-weight: 600;">{{ project.title }}</p> 
            <p>{{ project.decsription }}</p>
            <v-card-actions>
              <v-btn text target="_blank" :href="project.link">Visit</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <!-- Cards Row -->
    </v-container>

  </v-main>
</template>
  
<script>
export default {
  data() {
    return {
      projects: []
    };
  },
  mounted() {
    // Fetch projects and populate the data
    fetch('https://raw.githubusercontent.com/gandhirishi123/projectdata/main/projects.json')
      .then(response => response.json())
      .then(data => {
        this.projects = data;
      })
      .catch(error => {
        console.error('Error fetching projects:', error);
      });
  }
};
</script>
  
<style>
/* Add any custom styles here */
</style>
  