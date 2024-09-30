<template>
  <v-main class="pa-0 ma-0">
    <v-container class="my-3">
      <!-- HERO Section -->
      <v-row justify="center" align="center">
        <v-col md="10" class="text-center">
          <v-img
            :src="person.image_url"
            class="rounded-circle mb-3"
            alt=""
            style="width: 15%; margin-left: auto; margin-right: auto"
          ></v-img>
          <h1>{{ person.name }}</h1>
          <p>{{ person.city }}, {{ person.state }}, {{ person.country }}</p>
          <p>{{ person.short_bio }}</p>
          <v-btn
            class=""
            :href="'mailto:' + person.email"
            target="_blank"
            color="primary"
            depressed
            rounded
          >
            Contact Me</v-btn
          >
        </v-col>
      </v-row>
      <v-row>
       <v-col md="12" cols="12" justify="center" align="center">
       <a href="https://github.com/rishigandhi612">
         <v-icon class="mr-2">mdi-github</v-icon>
       </a>
       <a href="https://twitter.com/rishigandhi612">
         <v-icon class="mr-2">mdi-twitter</v-icon>
       </a>
       <a href="https://www.linkedin.com/in/rishigandhi612/">
         <v-icon>mdi-linkedin</v-icon>
       </a>
      </v-col>
   </v-row>
      <!-- HERO Section -->
      <!-- Projects Section -->
      <v-row style="background-color: white; border-radius: 15px" class="my-10">
        <v-col cols="12" md="12">
          <v-container fluid>
            <!-- Project Header -->
            <v-row>
              <v-col md="12">
                <h1>My Projects</h1>
                <p>
                  I've worked on various projects and based on my expertise and
                  current experience here are top 3 of them
                </p>
              </v-col>
            </v-row>
            <!-- Project Header -->
            <!-- Project Cards -->
            <v-row>
              <v-col
                v-for="(p, index) in projects"
                :key="index"
                cols="12"
                md="4"
              >
                <v-card
                  style="
                    height: 100%;
                    display: flex;
                    flex-direction: column;
                    justify-content: space-between;
                    border-radius: 15px;
                    background-color: #f3f6fc;
                  "
                  elevation="0"
                  class="pa-1"
                >
                  <v-card-title class="mb-0">{{ p.title }}</v-card-title>
                  <v-card-text class="mt-0">{{ p.decsription }}</v-card-text>
                  <v-card-actions>
                    <a :href="p.link" target="_blank">
                      <v-btn text>Visit</v-btn>
                    </a>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
      <!-- Projects Section -->
      <!-- Skills Section -->
      <v-row justify="center" align="center">
        <v-col md="8" class="text-center">
          <h1 style="text-align: center">
            Technologies I'm currently dealing with
          </h1>
          <p>
            I've been fascinated by technology since I was a young child, so
            I've always wondered how things function. I use new age technologies
            that are already available because I am an avid learner to make and
            create new things.
          </p>
          <v-chip
            class="mx-2 mb-2"
            v-for="(skill, index) in person.skills"
            :key="index"
            color="#ffc107"
          >
            {{ skill }}
          </v-chip>
        </v-col>
      </v-row>
      <!-- Skills Section -->
      <!-- Email Section -->
      <v-row>
        <v-col cols="12" class="text-center">
          <p class="mb-0">
            You can also contact me <a :href="'mailto:' + person.email">here</a>
          </p>
        </v-col>
      </v-row>
      <!-- Email Section -->
    </v-container>
  </v-main>
</template>

<script>
import mydata from "@/assets/data.json";
export default {
  data() {
    return {
      person: mydata,
      projects: [],
      drawer: false,
    };
  },
  methods: {
    getProjects() {
      fetch(
        "https://raw.githubusercontent.com/gandhirishi123/webapp-data/main/projects.json"
      )
        .then((data) => data.json())
        .then((res) => {
          this.projects = res;
        })
        .catch((err) => console.log(err));
    },
  },
  mounted() {
    this.getProjects();
  },
};
</script>

<style>
/* Add your custom styles here */
</style>
