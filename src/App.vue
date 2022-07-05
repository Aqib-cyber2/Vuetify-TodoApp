<template>
  <v-app :style="{background: $vuetify.theme.themes[theme].secondary}">
    <v-navigation-drawer app v-model="drawer" color="#005466" dark>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>
            TODO App
          </v-list-item-title>
          <v-list-item-subtitle>
            subtext
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>

        <v-list-item v-for="item in items" :key="item.title" link :to="item.to">

          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>

        </v-list-item>

      </v-list>

    </v-navigation-drawer>


    <v-app-bar app color="primary" dark src="header.jpg" prominent>

      <template v-slot:img="{ props }">
        <v-img v-bind="props" gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"></v-img>
      </template>

      <v-app-bar-nav-icon @click.stop="toggle"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-app-bar-title class="mx-auto">
        <p>Vuetify Todo App</p>
      </v-app-bar-title>
      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>

</template>

<script>
  export default {
    name: 'App',

    data: () => {
      return {
        drawer: null,
        items: [{
            title: 'Dashboard',
            icon: 'mdi-format-list-checks',
            to: '/'
          },
          {
            title: 'About',
            icon: 'mdi-help-box',
            to: '/about'
          },
        ],
      }
    },

    computed: {
      theme() {
        return (this.$vuetify.theme.dark) ? 'dark' : 'light'
      }
    },

    methods: {
      toggle() {
        this.drawer = !this.drawer
        console.log(this.drawer)
      }
    }
  };
</script>