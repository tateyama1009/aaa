<template>
  <v-app>
    <v-navigation-drawer class="orange darken-4" v-model="drawer" app clipped dark>
      <v-container>
        <v-list-item-content>
          <v-list-item-title class="title white--text">
            Menu
          </v-list-item-title>
        </v-list-item-content>
        <v-divider></v-divider>
        <v-list dense nav>
          <v-list-item v-for="nav_list in nav_lists" :key="nav_list.name">
            <v-list-item-icon>
              <v-icon>{{ nav_list.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-container>
    </v-navigation-drawer>
    <v-app-bar
      app
      color="orange derken-5"
      dark
      clipped-left
    >
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Tinker</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn text>Sign in</v-btn>
        <v-btn text>Sign up</v-btn>
      </v-toolbar-items>
    </v-app-bar>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>

export default {
  data () {
    return {
      drawer: null,
      nav_lists: [
        { name: 'Getting Started', icon: 'mdi-vuetify' },
        { name: 'Customization', icon: 'mdi-cogs' },
        { name: 'Styles & animations', icon: 'mdi-palette' }
      ]
    }
  }
}
</script>
