<template>
  <v-layout>
      <v-card
        elevation="2"
        tile
        width="100%"
      >
        <v-card-text v-html="document.headline+'<br/>'+document.path"></v-card-text>
        <v-card-actions>
          <v-btn
            text
            color="blue"
            @click="$set(document,'showed', !document.showed)"
          >
            {{ !document.showed ? 'Просмотр изображения' : 'Свернуть' }}
          </v-btn>
          <v-btn
            text
            color="blue"
            :href="appHost+'/documents/'+document.id"
            download
          >
            Скачать
          </v-btn>
      </v-card-actions>
      <v-img
        v-if="document.showed"
        :src="appHost+'/documents/'+document.id"
      ></v-img>
      </v-card>
  </v-layout>
</template>

<script>
export default {
  props: ["document", "loading"],
  data() {
    return {
      appHost: process.env.VUE_APP_HOST,
    }
  },
  methods: {
    async loadImage(document) {
      // this.$set(this.loading, true)
      this.axios
        .get(process.env.VUE_APP_HOST+"/documents/"+document.id)
        .then((r) => {
          document.data = r.data;
        })
        .finally(() => {
          // this.$set(this.loading, false)
        })
    },
  },
}
</script>

<style>

</style>