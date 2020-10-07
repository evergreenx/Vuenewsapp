<template>
  <v-app>
    <v-app-bar fixed dark app clipped-left class="elevation-2 red">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <!-- <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon> -->
      <v-toolbar-title class="white--text">News App</v-toolbar-title>
    </v-app-bar>

    <SideNav
      :drawer="drawer"
      :apikey="apikey"
      @selectSource="setNewsResource"
    />

    <v-container fluid>
      <v-main>
        <MainContent :articles="article" />
      </v-main>
    </v-container>
  </v-app>
</template>

<script>
import MainContent from "./components/MainContent";
import SideNav from "./components/SideNav";
import axios from "axios";

export default {
  name: "App",

  components: {
    MainContent,
    SideNav,
  },

  data: () => ({
    drawer: true,

    article: [],
    apikey: "5ebdd2c815384793a582b2071f9a746c",

    //
  }),

  created() {
    axios
      .get(
        "http://newsapi.org/v2/everything?" +
          "sources=bbc-news&" +
          "pageSize=70&" +
          "apiKey=5ebdd2c815384793a582b2071f9a746c"
      )
      .then((res) => {
        this.article = res.data.articles;
      });
  },

  methods: {
    setNewsResource(source) {
      axios
        .get(
          "http://newsapi.org/v2/top-headlines?" +
            "sources=" +
            source +
            "&apiKey=5ebdd2c815384793a582b2071f9a746c"
        )
        .then((res) => {
          this.article = res.data.articles;
        });
    },
  },
};
</script>
