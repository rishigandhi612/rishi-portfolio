<template>
  <v-main class="pa-0 ma-0">
    <v-container class="my-3">
      <!-- Header Row -->
      <v-row>
        <v-col cols="12" md="3">
          <div>
            <v-img
              :src="person.image_url"
              style="background-color: white; border-radius: 15px"
            ></v-img>
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
          </div>
        </v-col>
        <v-col md="9">
          <div
            style="background-color: white; border-radius: 15px"
            class="pa-5"
          >
            <p class="mb-0">{{ person.bio }}</p>
          </div>
          <p class="mb-0 mt-10" style="font-weight: 600; font-size: 120%">
            My Community Experience
          </p>
          <v-container fluid class="px-0">
            <v-row>
              <v-col
                cols="12"
                v-for="(item, index) in experience"
                :key="index"
                md="4"
              >
                <div
                  style="background-color: white; border-radius: 15px"
                  class="pa-5"
                >
                  <p style="font-weight: 600; font-size: 110%" class="mb-0">
                    {{ item.title }}
                  </p>
                  <p class="mb-0">{{ item.desc }}</p>
                  <p class="mb-0 mt-2 text--secondary" style="font-size: 70%">
                    {{ item.period }}
                  </p>
                </div>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
      <!-- Header Row -->
    </v-container>
  </v-main>
</template>

<script>
import mydata from "@/assets/data.json";
export default {
  data: () => ({
    person: mydata,
    experience: [],
  }),
  created() {
    this.getVolunteerExperience();
  },
  methods: {
    async getVolunteerExperience() {
      try {
        const response = await fetch(
          "https://raw.githubusercontent.com/gandhirishi123/volunteerdata/main/community.json"
        );
        const data = await response.json();
        this.experience = data;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style></style>
