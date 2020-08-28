<template>
  <v-app>
    <v-app-bar
      app
      color="purple darken-4"
      dark
    >
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>Vuetify</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 2"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list
        nav
        dense
      >
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

    <v-main>
      <v-container>
        <v-row>
          <v-col 
            sm="auto"
            cols="12"
          >  
            <Images/>
          </v-col>
          <v-col 
            sm
            cols="12"
          >
            <Alerts/>
          </v-col>
        </v-row>
       
        <v-parallax
          :height="height"
          src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"
        >
          <v-row
            align="stretch"
            justify="center"
          >
            <v-col
              v-for="n in 3"
              :key="n"
              :sm="cols[n-1]"
              :md="cols[n-1]"
              :lg="cols[n-1]"
              cols="12"
            >
              <v-card
                class="pa-2"
                outlined
                tile
                height="100%"
              >
                .col-{{cols[n-1]}}
              </v-card>
            </v-col>
          </v-row>
        </v-parallax>

        <v-row>
          <v-col>
            <v-btn-toggle
              v-model="text"
              tile
              color="deep-purple accent-3"
              group
            >
              <v-btn value="left">Left</v-btn>
              <v-btn value="center">Center</v-btn>
              <v-btn value="right">Right</v-btn>
              <v-btn value="justify">Justify </v-btn>
            </v-btn-toggle>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Images from './components/Images';
import Alerts from "./components/Alerts";
export default {
  name: 'App',
  components: {
    Images, 
    Alerts, 
  },

  data: () => ({
    drawer:false,
    group:'',
    height:'200',
    text:''
  }),

  computed: {
    cols() {
      // let vm=this;
      const { lg, md, sm } = this.$vuetify.breakpoint;
      if(lg) return ['2', '8', '2'];
      if(md) return ['3', '6', '3'];
      if(sm) return ['4', '4', '4'];
      return ['12', '12', '12']
    }
  },
};
</script>
