<template>
  <v-layout>
    <v-container>
      <v-layout column class="pt-5">
        <SearchBar @search="search" :loading="loading"></SearchBar>
        <div v-if="'totalRecords' in pagination">
          Найдено {{ pagination.totalRecords }} {{ declOfNum(pagination.totalRecords, ['совпадение', 'совпадения', 'совпадений']) }}
        </div>
        <v-container v-for="document in currentDocuments" :key="document.id">
          <ResponseListItem :document="document" :loading="loading"></ResponseListItem>
        </v-container>
      </v-layout> 
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
    declOfNum(n, text_forms) {  
      n = Math.abs(n) % 100; var n1 = n % 10;
      if (n > 10 && n < 20) { return text_forms[2]; }
      if (n1 > 1 && n1 < 5) { return text_forms[1]; }
      if (n1 == 1) { return text_forms[0]; }
      return text_forms[2];
    },
  },
  computed: {
    
  },
  components: {
    SearchBar,
    ResponseListItem,
  }

}
</script>

<style>

</style>