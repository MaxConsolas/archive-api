<template>
  <v-app>
    <v-main>
      <NavBar/>
      <Main/>
      <Footer/>
    </v-main>
  </v-app>
</template>

<script>
import NavBar from './components/NavBar';
import Main from './components/Main';
import Footer from './components/Footer';

export default {
  name: 'App',

  components: {
    NavBar,
    Main,
    Footer,
  },

  data: () => ({
    //
  }),
};
</script>
