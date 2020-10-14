<template>
<div>

 
  <div  v-if="this.articles">
    <v-card
      hover
      class="mx-auto mt-4"
      max-width="644"
      v-for="article in articles"
      :key="article.title"
    >
      <v-img :src="article.urlToImage" height="200px"></v-img>

      <v-card-title>
        {{ article.title }}
      </v-card-title>

      <v-card-subtitle>
        {{ article.source.name }}
      </v-card-subtitle>

      <v-card-subtitle>
    
      </v-card-subtitle>

<div>
          <v-divider></v-divider>
<br/>
          <v-card-text>
            {{ article.description }}
            <v-btn
              small
              replace
              color="blue"
              v-bind:href="article.url"
              target="_blank"
              >Read More</v-btn
            >

            <v-spacer></v-spacer>
          </v-card-text>
        </div>
      <v-card-actions>
        <v-spacer></v-spacer>

        <!-- <v-btn icon @click="show = !show">
          <v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
        </v-btn> -->
      </v-card-actions>

      <v-expand-transition>
        
      </v-expand-transition>
    </v-card>

  </div>
   <div v-else>

   
  <v-sheet
    :color="grey"
    class="pa-3"
  >
    <v-skeleton-loader
      class="mx-auto"
      max-width="300"
      type="card"
    ></v-skeleton-loader>
  </v-sheet>

  </div>
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
  methods: {

    convertdate(){
      const dateString =this.articles.publishedAt;
      const localDate = new Date(`${dateString} UTC`);
      console.log(localDate)
    }
  },
};
</script>

<style lang="scss" scoped></style>
