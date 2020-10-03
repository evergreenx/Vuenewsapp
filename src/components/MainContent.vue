<template>
  <div>
    <h1>Hello</h1>


    <v-card hover class="mx-auto mt-4" max-width="644" v-for="article in articles" :key='article.title'>
      <v-img :src="article.urlToImage" height="200px"></v-img>

      <v-card-title>
       {{article.title}}
      </v-card-title>

      <v-card-subtitle>
        1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange lighten-2" text>
          Explore
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
         {{article.description}}

<v-spacer></v-spacer>
           <v-btn small replace color="red" v-bind:href="article.url" target="_blank" >Read More</v-btn>

          </v-card-text>

        </div>
      </v-expand-transition>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "MainContent",

  data() {
    return {

      show: false,
    };
  },
  props: {
    articles: Array,
    
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
