<template>
 <v-app-bar app color="white" flat>
        <v-toolbar-title class="ml-4">Rishi Gandhi</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn class="ml-3" v-model="isNavOpen" app v-for="item in navItems" :key="item.text" :to="item.link" text
          @click="closeNav" active-class="blue lighten-5" rounded>
          {{ item.text }}
        </v-btn>
      </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      isNavOpen: false,
      navItems: [
        { text: 'Home', link: '/' },
        { text: 'Projects', link: '/project' },
        { text: 'About', link: '/about' }
      ],
    };
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen;
    },
    closeNav() {
      this.isNavOpen = false;
    },
  },
};
</script>
