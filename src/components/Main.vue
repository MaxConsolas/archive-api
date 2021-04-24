<template>
  <v-layout>
    <v-container>
      <v-row class="pt-5">
        <SearchBar @search="search" :loading="loading"></SearchBar>
        <v-container v-for="document in currentDocuments" :key="document.id">
          <ResponseListItem :document="document" :loading="loading"></ResponseListItem>
        </v-container>
      </v-row> 
    </v-container>
  </v-layout>
</template>

<script>
import SearchBar from "./Main/SearchBar"
import ResponseListItem from "./Main/ResponseListItem"

export default {
  data() {
    return {
      currentDocuments: [],
      pagination: {},
      loading: false,
    }
  },
  methods: {  
    search(input) {
      this.loading = true;
      this.axios
        .get(process.env.VUE_APP_HOST+"/search", {params: {searchRequest: input, limit: 10, offset: 0}})
        .then((r) => {
          // console.log(r.data.documents)
          this.currentDocuments = r.data.documents;
          this.pagination = r.data.pagination;
        })
        .finally(() => {
          this.loading = false;
        })
    },
  },
  components: {
    SearchBar,
    ResponseListItem,
  }

}
</script>

<style>

</style>