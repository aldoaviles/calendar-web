<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        Calendario
      </div>
      <v-spacer></v-spacer>
      <span class="mr-2">Versión 1.0</span>
    </v-app-bar>
    <v-main>
      <Calendario />
    </v-main>
  </v-app>
</template>

<script>
import Calendario from "./components/Calendario";

export default {
  name: "App",

  components: {
    Calendario
  },

  data: () => ({
    //
  }),
};
</script>
