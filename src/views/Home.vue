<template>
  <div>
    <p>This is chat page</p>
    <v-bottom-navigation absolute min-height>
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
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>
