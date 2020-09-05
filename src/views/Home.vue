<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Calendario msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import Calendario from "@/components/Calendario.vue";

export default {
  name: "Home",
  components: {
    Calendario
  }
};
</script>
