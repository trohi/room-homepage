<template>
  <v-app>
    <v-main>
      <Home2/>
    </v-main>
  </v-app>
</template>

<script>
import Home from './components/Home';
import Home2 from './components/Home2';

export default {
  name: 'App',

  components: {
    Home,
    Home2
  },

  data: () => ({
  }),
};
</script>
