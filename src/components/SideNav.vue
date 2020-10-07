<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app clipped>
      <v-list nav dense class="pt-3">
        <v-list-item-group
          
          active-class="deep-purple--text text--accent-4"
          v-for="source in sources" :key="source.id"
        >
          
          <v-tooltip bottom>

<template v-slot:activator="{on , attrs}">
          <v-list-item 
          @click="selectSource(source.id)"
v-bind="attrs"
v-on="on"
          
          
          >


            <v-avatar>
              <img :src="imageUrl(source.id)" class="mb-2 img circle elevation-7" />
              <!-- <v-icon>mdi-home</v-icon> -->
            </v-avatar>
            <v-list-item-title>{{ source.name }}</v-list-item-title>


        

          </v-list-item>
</template>

<span> {{source.name}}</span>
</v-tooltip>


        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SideNav",
  created() {
    axios
      .get(
        "https://newsapi.org/v2/sources?language=en&apiKey=" +
          "5ebdd2c815384793a582b2071f9a746c"
      )
      .then((res) => {
      
        this.sources = res.data.sources;
      });
  },
  data() {
    return {
      draw: this.drawer,
      sources: [],
    };
  },
  props: {
    drawer: Boolean,
   
    apikey: String,
  },
  methods: {
    imageUrl(pic) {
      return require("../assets/images/" + pic + ".png");
    },
    selectSource(source){
      this.$emit('selectSource' , source)
      
    }
  },
};
</script>

<style lang="scss" scoped></style>
