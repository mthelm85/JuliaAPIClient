<template>
  <v-app>
    <v-content>
      <Add />
    </v-content>
  </v-app>
</template>

<script>
import Add from './components/Add';

export default {
  name: 'App',

  components: {
    Add,
  },

  data: () => ({
    //
  }),
};
</script>
