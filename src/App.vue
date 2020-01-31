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
        <v-list-item v-model="user">
          <v-list-item-icon>
            <v-icon>{{ user.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-title class="white--text">
            {{ user.username }}
          </v-list-item-title>
        </v-list-item>
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

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
import { mdiSettingsTransfer } from '@mdi/js'
import { mdiFreebsd } from '@mdi/js'
import { mdiCheckboxMultipleBlank } from '@mdi/js'
import { mdiAccountCircleOutline } from '@mdi/js'
export default {
  data() {
    return {
      drawer: null,
      nav_lists: [
        { name: 'Channels', icon: mdiCheckboxMultipleBlank },
        { name: 'friends', icon: mdiFreebsd },
        { name: 'Settings', icon: mdiSettingsTransfer }
      ],
      user: { username: 'username', icon: mdiAccountCircleOutline }
    }
  }
}
</script>
