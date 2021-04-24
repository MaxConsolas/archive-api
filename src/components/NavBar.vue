<template>
  <v-layout>
  <v-toolbar dark color="primary">
    <v-toolbar-title class="white--text">{{ appName }}</v-toolbar-title>
  </v-toolbar>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      appName: process.env.VUE_APP_NAME,
    }
  },
  methods: {
  },
}
</script>

<style>

</style>