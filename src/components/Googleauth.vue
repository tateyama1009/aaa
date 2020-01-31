<template>
  <v-app>
    <v-btn class="ma-4" @click="authFunction">
      or, from Google account
      <v-icon color="blue darken-2" right>
        {{ icons.mdiGoogle }}
      </v-icon>
    </v-btn>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      userName: null,
      userPic: null,
      isSignedIn: null,
      authButtonText: null,
      authFunction: function() {}
    }
  },
  created() {
    this.onAuthStateChanged()
  },
  methods: {
    onAuthStateChanged() {
      firebase.auth().onAuthStateChanged(user => {
        this.userName = user ? this.getUserName() : null
        this.userPic = user ? this.getProfilePicUrl() : null
        this.authButtonText = user ? 'Sign-out' : 'Sign-in with Google'
        this.authFunction = user ? this.signOut : this.signIn
        this.isSignedIn = user ? true : false
      })
    },
    signIn() {
      const provider = new firebase.auth.GoogleAuthProvider()
      firebase.auth().signInWithPopup(provider)
    },
    signOut() {
      firebase.auth().signOut()
    },
    isUserSignedIn() {
      return !!firebase.auth().currentUser || false
    },
    getProfilePicUrl() {
      return (
        firebase.auth().currentUser.photoURL ||
        '/static/images/profile_placeholder.png'
      )
    },
    getUserName() {
      return firebase.auth().currentUser.displayName
    }
  }
}
</script>
