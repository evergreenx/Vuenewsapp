<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app clipped>
      <v-list nav dense class="pt-3">
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item v-for="source in sources" :key="source.id">
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>{{source.name}}</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Account</v-list-item-title>
          </v-list-item>
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
        "https://newsapi.org/v2/sources?apiKey=" +
          "5ebdd2c815384793a582b2071f9a746c"
      )
      .then((res) => {
        console.log(res);
        this.sources = res.data.sources
      });
  },
  data() {
    return {
      draw: this.drawer,
      sources:[]
    };
  },
  props: {
    drawer: Boolean,
    group: null,
    apikey: String,
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
