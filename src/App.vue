<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      class="orange darken-4"
      app
      clipped
      dark
    >
      <v-container>
        <v-list-item-content>
          <v-list-item-title class="title white--text">
            Menu
          </v-list-item-title>
        </v-list-item-content>
        <v-divider />
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
    <v-app-bar app dense color="orange derken-5" dark clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-toolbar-title>
        <router-link to="/" tag="v-toolbar-title">
          Tinker
        </router-link>
      </v-toolbar-title>
      <v-spacer />
      <v-toolbar-items>
        <v-btn text to="/signin">
          Sign in
        </v-btn>
        <v-btn text to="/signup">
          Sign up
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <v-bottom-navigation app min-height>
      <v-textarea
        clearable
        append-outer-icon="mdi-send"
        auto-grow
        row-height="8"
        label="Your message"
        single-line
        filled
        dense
      />
    </v-bottom-navigation>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
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
