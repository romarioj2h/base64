<template>
  <v-app id="app" :dark="mode">
    <v-navigation-drawer temporary clipped-left app v-model="drawer">
      <v-list two-line>
        <v-list-tile
          v-for="(item, index) in items"
          :key="index"
          :to="item.route"
        >
          <v-list-tile-content>
            <v-list-tile-title v-html="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile>
          <v-list-tile-content>
            <v-switch
              v-model="mode"
              :label="`${mode ? 'Dark' : 'Light'} Mode`"
              hide-details
            ></v-switch>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="indigo" dark fixed app>
      <v-toolbar-side-icon @click="drawer = !drawer;"></v-toolbar-side-icon>
      <v-toolbar-title>Base64<v-icon>swap_horiz</v-icon>Texto</v-toolbar-title>
    </v-toolbar>
    <v-content>
      <v-container fluid fill-height>
        <v-layout justify-center align-center>
          <v-flex text-xs-center> <router-view></router-view> </v-flex>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer
      class="px-3 d-flex justify-content-between white--text"
      color="indigo"
      app
    >
      <span v-html="copy"></span>
      <span class="text-xs-right">Huebra developer</span>
    </v-footer>
  </v-app>
</template>

<script>
import Base64 from "./components/Base64";

export default {
  name: "App",
  components: {
    Base64
  },
  computed: {
    copy() {
      return `&copy; ${new Date().getFullYear()}`;
    }
  },
  data() {
    return {
      drawer: false,
      mode: false,
      items: [
        {
          route: "/",
          title: "Base 64"
        }
      ]
    };
  }
};
</script>
