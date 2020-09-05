<template>
  <v-container>
    <v-row>
      <v-col>
        <v-sheet height="64">
          <v-toolbar flat color="white">
            <v-btn fab color="withe" @click="anterior">
              <v-icon small>mdi-chevron-left</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-toolbar-title v-if="$refs.calendarActual">
              {{ $refs.calendarActual.title }}
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn fab color="withe" @click="siguiente">
              <v-icon small>mdi-chevron-right</v-icon>
            </v-btn>
          </v-toolbar>
        </v-sheet>
      </v-col>
    </v-row>
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
  name: "Calendario",
  data: () => ({
    mesAnterior: null,
    mesActual: null,
    mesSiguiente: null,
  }),
  methods: {
    anterior() {
      this.mesAnterior = this.restaMes(new Date(this.mesAnterior));
      this.mesActual = this.restaMes(new Date(this.mesActual));
      this.mesSiguiente = this.restaMes(new Date(this.mesSiguiente));
    },
    siguiente() {
      this.mesAnterior = this.agregaMes(new Date(this.mesAnterior));
      this.mesActual = this.agregaMes(new Date(this.mesActual));
      this.mesSiguiente = this.agregaMes(new Date(this.mesSiguiente));
    },
    agregaMes(fecha) {
      fecha.setMonth(fecha.getMonth() + 1);
      return fecha;
    },
    restaMes(fecha) {
      fecha.setMonth(fecha.getMonth() - 1);
      return fecha;
    },
  },
  mounted() {
    this.mesAnterior = this.restaMes(new Date());
    this.mesActual = new Date();
    this.mesSiguiente = this.agregaMes(new Date());
  },
};
</script>
