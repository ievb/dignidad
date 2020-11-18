<!-- To run: $ npm run electron:serve -->
<template>
  <v-container class="fs-10">
    <h1>Elecciones 2020</h1>


    <v-expansion-panels focusable inset>
      <v-expansion-panel v-for="acta in actas" :key="acta.codigoMesa">
        <v-expansion-panel-header>
           Acta: {{ acta.codigoMesa }}
          <v-chip class="ma-2 mw-80" color="green" text-color="green" align="right" outlined x-small>
            Presidencial
          </v-chip>
          <v-chip class="ma-2 mw-80" color="orange" text-color="orange" align="right" outlined x-small>
            Uninominal
          </v-chip>
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <div v-for="child in acta.datoAdicional.tabla" :key="child.nombre">
            {{ child.nombre }}
            <v-chip class="ma-2" color="green" text-color="green" outlined x-small>
              {{ child.valor1 }}
            </v-chip>
            <v-chip class="ma-2" color="orange" text-color="orange" outlined x-small>
              {{ child.valor2 }}
            </v-chip>
          </div>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </v-container>
</template>

<script>
const axios = require("axios");
export default {
  name: "Index",

  data() {
    return {
      actas: [],
    };
  },
  created() {
    var x = {
      fecha: "17/11/2020 22:01:01",
      correcto: true,
      notificacion: "Transacción satisfactoria",
      datoAdicional: {
        tabla: [
          {
            nombre: "CREEMOS",
            valor1: "0",
            valor2: "4",
            valor3: null,
          },
          {
            nombre: "ADN",
            valor1: "0",
            valor2: null,
            valor3: null,
          },
          {
            nombre: "MAS-IPSP",
            valor1: "150",
            valor2: "133",
            valor3: null,
          },
          {
            nombre: "FPV",
            valor1: "5",
            valor2: "2",
            valor3: null,
          },
          {
            nombre: "PAN BOL",
            valor1: "3",
            valor2: null,
            valor3: null,
          },
          {
            nombre: "LIBRE 21",
            valor1: "0",
            valor2: "0",
            valor3: null,
          },
          {
            nombre: "CC",
            valor1: "43",
            valor2: "41",
            valor3: null,
          },
          {
            nombre: "JUNTOS",
            valor1: "0",
            valor2: "0",
            valor3: null,
          },
          {
            nombre: "Votos Válidos",
            valor1: "201",
            valor2: "180",
            valor3: null,
          },
          {
            nombre: "Votos Blancos",
            valor1: "1",
            valor2: "23",
            valor3: null,
          },
          {
            nombre: "Votos Nulos",
            valor1: "3",
            valor2: "2",
            valor3: null,
          },
          {
            nombre: "Votos Emitidos",
            valor1: "205",
            valor2: "205",
            valor3: null,
          },
        ],
        observacion: "Ver documentos adjuntos",
        adjunto: [
          {
            tipo: "ACTA",
            valor: "https://s3.amazonaws.com/archivo.computo/actas/25569.jpg",
          },
          {
            tipo: "PROVEIDO",
            valor: true,
          },
          {
            tipo: "RESOLUCION",
            valor: false,
          },
        ],
      },
    };
    x = { ...x, codigoMesa: "123" };
    this.actas.push(x);
    console.info("fecha: ", this.actas);
    console.dir(x);
    /*
      axios.post('https://computo.oep.org.bo/api/v1/resultado/mesa', {"codigoMesa": "25569"})
        .then(response => {
          console.info('data', response.data);
          this.actas = { ...response.data, codigoMesa: '123' };
          //actas = response.data
          console.info('actas.datoAdicional.tabla', this.actas.datoAdicional.tabla)
        });
      */
  },
};
</script>
<style scoped>
  .fs-10 {font-size: 10px;}
  .mw-80 {max-width: 80px;}
</style>
