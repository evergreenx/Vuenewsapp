<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app clipped 
      >
      <v-list nav dense class="pt-3">
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
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
export default {
  name: "SideNav",
  created() {},
  data() {
    return {

      draw:this.drawer
    };
  },
  props: {
    drawer: Boolean,
    group: null,
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
