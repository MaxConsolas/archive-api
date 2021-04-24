<template>
  <v-layout>
      <v-text-field
          label="Поисковый запрос"
          placeholder="Введите сдесь ваш запрос" 
          clearable
          hide-details
          v-model="inputQuery"
          autofocus
          @keydown="searchOnEnter"
        >
        </v-text-field>
        <v-btn
          x-large
          outlined
          class="ml-5"
          color="blue"
          @click="$emit('search', inputQuery)"
          :loading="loading"
        >Поиск
        </v-btn>
  </v-layout>
</template>

<script>
export default {
  props: ["loading"],
  data() {
    return {
      inputQuery: null,
    }
  },
  methods: {
    searchOnEnter(key) {
      if (key.key == "Enter") {
        this.$emit("search", this.inputQuery);
      }
    },
  },
}
</script>

<style>

</style>