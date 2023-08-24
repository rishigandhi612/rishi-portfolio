<template>
    <v-container class="text-center my-5">
      <v-row >
        <v-col cols="12">
          <h1>Me, Myself & I</h1>
          <v-container>
            <v-row>
              <v-col cols="12">
                <h4>Technologies I'm currently dealing with</h4>
                <p>I've been fascinated by technology since I was a young child, so I've always wondered how things
                  function. I use new age technologies that are already available because I am an avid learner to make
                  and create new things.</p>
                <h6>Turning ideas into reality is my calling.</h6>
                <div id="skillset">
                  <v-chip v-for="skill in person1.skillset" :key="skill" class="mx-1">{{ skill }}</v-chip>
                </div>
              </v-col>
              <v-col cols="12" class="my-5 text-center" id="about">
                <v-row>
                  <v-col v-for="exp in experience" :key="exp.title" cols="12" md="4">
                    <v-card class="mx-3">
                      <v-row no-gutters>
                        <v-col cols="4">
                          <v-img :src="exp.src" class="img-fluid rounded-start"></v-img>
                        </v-col>
                        <v-col cols="8">
                          <v-card-title>{{ exp.title }}</v-card-title>
                          <v-card-text>{{ exp.desc }}</v-card-text>
                          <v-card-subtitle>{{ exp.period }}</v-card-subtitle>
                        </v-col>
                      </v-row>
                    </v-card>
                  </v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        person1: {
          skillset: ["HTML:5", "CSS:3", "JavaScript", "Embedded C", "MySQL", "Data Structures", "C++", "Java"],
        },
        experience: [],
      };
    },
    created() {
      this.getVolunteerExperience();
    },
    methods: {
      async getVolunteerExperience() {
        try {
          const response = await fetch('https://raw.githubusercontent.com/gandhirishi123/volunteerdata/main/community.json');
          const data = await response.json();
          this.experience = data;
        } catch (error) {
          console.error(error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  
  
  #skills {
    padding-bottom: 0%;
  }
  
  .v-chip {
    font-size: 20px;
    border: 1px solid black;
    font-weight: 300;
    text-decoration: solid;
    color: black;
  }
  
  .v-card {
    border: 1px solid black;
  }
  
  #proo {
    border: 1px solid black;
    background-color: #e0e0e0;
  }
  
  .contact {
    border: 1px solid black;
  }
  
  #skillset {
    padding-bottom: 0%;
  }
  </style>
  