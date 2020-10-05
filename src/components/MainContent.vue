<template>
  <div>
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
        {{ article.author }}
      </v-card-subtitle>

      <v-card-subtitle>
        {{convertdate}}
      </v-card-subtitle>

<div>
          <v-divider></v-divider>

          <v-card-text>
            {{ article.description }}
            <v-btn
              small
              replace
              color="red"
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
