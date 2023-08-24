<template>
  <v-app style="background-color: #f3f6fc;">
   <NavBar/>
    <v-main>
      <v-slide-y-reverse-transition>
        <router-view/>
      </v-slide-y-reverse-transition>
     
    </v-main>
  </v-app>
</template>

<script>

import NavBar from './components/NavBar.vue';
export default {
  name: 'App',
  components:{
    NavBar
  },
  data: () => ({
    //
  }),
};
</script>
