<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <v-sheet height="64">
          <v-toolbar flat color="white">
            <v-toolbar-title v-if="$refs.calendarAnterior">
              {{ $refs.calendarAnterior.title }}
            </v-toolbar-title>
            <v-spacer></v-spacer>
          </v-toolbar>
        </v-sheet>
        <v-calendar
          v-model="mesAnterior"
          locale="es"
          ref="calendarAnterior"
          color="accent"
        ></v-calendar>
      </v-col>
      <v-col>
        <v-sheet height="64">
          <v-toolbar flat color="white">
            <v-toolbar-title v-if="$refs.calendarActual">
              {{ $refs.calendarActual.title }}
            </v-toolbar-title>
            <v-spacer></v-spacer>
          </v-toolbar>
        </v-sheet>
        <v-calendar
          v-model="mesActual"
          locale="es"
          ref="calendarActual"
          color="primary"
        ></v-calendar>
      </v-col>
      <v-col>
        <v-sheet height="64">
          <v-toolbar flat color="white">
            <v-toolbar-title v-if="$refs.calendarSiguiente">
              {{ $refs.calendarSiguiente.title }}
            </v-toolbar-title>
            <v-spacer></v-spacer>
          </v-toolbar>
        </v-sheet>
        <v-calendar
          v-model="mesSiguiente"
          locale="es"
          ref="calendarSiguiente"
          color="accent"
        ></v-calendar>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => ({
    mesAnterior: "",
    mesActual: "",
    mesSiguiente: "",
  }),
  mounted() {
    let mesAnt = new Date();
    mesAnt.setMonth(mesAnt.getMonth() - 1);
    this.mesAnterior = mesAnt;

    let mesAct = new Date();
    this.mesActual = mesAct;

    let mesSig = new Date();
    mesSig.setMonth(mesSig.getMonth() + 1);
    this.mesSiguiente = mesSig;
  }
};
</script>
