<template>
  <div>
    <v-app>
      <v-container>
        <v-bottom-navigation absolute>
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
      </v-container>
    </v-app>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>
