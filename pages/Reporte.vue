<template>
  <v-row>
    <v-col class="text-center">
      <img src="/logo.png" alt="Vuetify.js" class="mb-5"/>
        <blockquote class="blockquote">
          <center>
            <v-col class="d-flex" cols="12" sm="3">
              <v-select
                :items="nameMes"
                filled
                label="Mes"
                class="text-md-center"
              ></v-select>
            </v-col>
          <a href="Javascript:window.open('VentanaReporte','','width=800, height=600');">
              <v-col  md="3">
                <v-btn  dark small color="gray"> 
                  Reporte
                <v-icon dark color="red">
                mdi-chart-box
                </v-icon>
                </v-btn>
              </v-col>
            </a>
          </center>
        </blockquote>
    </v-col>
  </v-row>  
</template>
  
  <script>
  export default {
    data: () => ({
    name: 'InspirePage',
    nameMes: ['Enero', 'Febrero'],
 
})
}
  </script>