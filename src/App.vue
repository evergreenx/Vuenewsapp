<template>
  <v-app>
    <v-app-bar fixed dark app clipped-left class="elevation-2 red">
     <v-app-bar-nav-icon @click="drawer =!drawer"></v-app-bar-nav-icon>

      <!-- <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon> -->
      <v-toolbar-title class="white--text">News App</v-toolbar-title>
    </v-app-bar>

    <SideNav :drawer="drawer" :group="group" />

    <v-container fluid>
      <v-main>
        <MainContent />
      </v-main>
    
    </v-container>
  </v-app>
  
</template>

<script>
import MainContent from "./components/MainContent";
import SideNav from "./components/SideNav";

export default {
  name: "App",

  components: {
    MainContent,
    SideNav,
  },

  data: () => ({
    drawer: true,
    group: null,

    //
  }),
};
</script>
