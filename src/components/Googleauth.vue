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
import { mdiGoogle } from '@mdi/js'
let firebase = require('firebase/app')
require('firebase/auth')
require('firebase/firebase-analytics')

// Your web app's Firebase configuration
let firebaseConfig = {
  apiKey: 'AIzaSyChjoNSAeSO1aB1x5BQeoLjmOMqCl02jWI',
  authDomain: 'aaa1-ac18a.firebaseapp.com',
  databaseURL: 'https://aaa1-ac18a.firebaseio.com',
  projectId: 'aaa1-ac18a',
  storageBucket: 'aaa1-ac18a.appspot.com',
  messagingSenderId: '971130358916',
  appId: '1:971130358916:web:ae7b3133cd30e87c4086d1',
  measurementId: 'G-NNMJLFQQBG'
}
// Initialize Firebase
firebase.initializeApp(firebaseConfig)
firebase.analytics()

export default {
  name: 'App',
  data() {
    return {
      userName: null,
      userPic: null,
      isSignedIn: null,
      authButtonText: null,
      authFunction: function() {},
      icons: {
        mdiGoogle
      }
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
