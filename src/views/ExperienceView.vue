<template>
  <v-main class="pa-0 ma-0">
    <v-container class="my-3">
      <!-- HERO Section -->
      <v-row justify="center" align="center">
        <v-col md="10" class="text-center">
          <h1>My Professional Experience</h1>
          <p>
            Currently, I have more than three years of internship experience.
            I'm actively looking for jobs as well as freelance work.
          </p>
        </v-col>
      </v-row>

      <!-- Experience Section -->
      <v-row>
        <v-col
          v-for="experience in experienceList"
          :key="experience.company_name"
          cols="12"
          md="12"
        >
          <v-card
            class="pa-5"
            style="
              height: 100%;
              display: flex;
              flex-direction: column;
              justify-content: space-between;
              background-color: white;
              border-radius: 15px;
              border: 0;
            "
            elevation="0"
            outlined
          >
          <p style="font-size: 120%; font-weight: 600">
              {{ experience.company_name }}
            </p>
            <p style="font-size: 120%; font-weight: 600">
              {{ experience.job_role }}
            </p>
          </v-card>
        </v-col>
      </v-row>
        <!-- Social Links Section -->
        <v-row>
        <v-col class="text-center">
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
          <v-row>
            <v-col class="text-center">
              <v-btn
                :href="'mailto:' + person.email"
                target="_blank"
                color="primary"
                depressed
                rounded
              >
                Contact Me
              </v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
import mydata from "@/assets/data.json";

export default {
  data() {
    return {
      person: mydata,
      experienceList: [],
      drawer: false,
    };
  },
  methods: {
    getExperience() {
    fetch("https://raw.githubusercontent.com/rishigandhi612/experiencedata/main/experience.json")
        .then((response) => {
            if (!response.ok) {
                throw new Error("Network response was not ok");
            }
            return response.json();
        })
        .then((res) => {
            this.experienceList = res;
            console.log("Data fetched successfully:", this.experienceList);
        })
        .catch((err) => console.error("Error fetching data:", err));
}
  },
  mounted() {
    this.getExperience();
  },
};
</script>

<style>
/* Add your custom styles here */
</style>
