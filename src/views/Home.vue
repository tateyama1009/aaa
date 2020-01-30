<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <v-app>
      <v-container>
        <v-bottom-navigation>
          <v-textarea
            clearable
            append-outer-icon="mdi-send"
            auto-grow
            row-height
            label="Your message"
            single-line
            filled
            dense
          >
          </v-textarea>
        </v-bottom-navigation>
      </v-container>
    </v-app>
  </div>

</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  }
}
</script>
