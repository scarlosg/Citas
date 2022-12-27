<template>
  <v-row> 
    <v-col class="text-center">
      <img src="/logo.png" alt="Vuetify.js" class="mb-5">

        
         

          <v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step
        :complete="e1 > 1"
        step="1"

      >
        Buscar Cédula
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step
        :complete="e1 > 2"
        step="2"
      >
        Name of step 2
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3">
        Name of step 3
      </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="250px"
        >
        <v-row justify="center" align="center">
        <v-col cols="12" sm="8">
          <v-form action=""  class="ma-6">
            <p>
              Buscar Cédula: <input v-mask="['#.###.###','##.###.###']" type="search"  name="buscarcedula" placeholder="V-">
                <v-btn dark small color="gray" height="25">Buscar
                  <v-icon dark>
                   mdi-account-search
                  </v-icon>
                </v-btn>
            </p>
            <br>
            <br>
            <br>
            <br>
            <p>Si no esta Registrado, Haga Click <a href="http://localhost:3000/RegistrarUs" target="_blank" rel="noopener noreferrer">Aquí</a></p>
                        
          </v-form>
   </v-col>
  </v-row>
      </v-card>

        <v-btn
          color="primary"
          @click="e1 = 2"
        >
          Siguiente
        </v-btn>

        
      </v-stepper-content>

      <v-stepper-content step="2">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="250px"
        >

        <v-row justify="center" align="center">
        <v-col cols="6" sm="3">      
          <v-select 
            :items="itemsM"
            label="Especialidad"
            outlined
          ></v-select>
        </v-col>
      </v-row> 
      <v-row justify="center" align="center">
<v-col class="d-flex" cols="6" sm="3">
          <v-select
            :items="itemsP"
            filled
            label="Medico"
            class="text-md-center"
          ></v-select>
        </v-col>
      </v-row>
      </v-card>

        <v-btn
          color="primary"
          @click="e1 = 3"
        >
          Continue
        </v-btn>

        <v-btn text @click="e1 = 1">
          Atras
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="3">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="400px"
        >
        
  <v-row justify="center">
    <v-date-picker  v-model="picker" locale="es"> 
    </v-date-picker>
  </v-row>

      </v-card>

        <v-btn
          color="primary"
          @click="e1 = 1"
        >
          Continue
        </v-btn>

        <v-btn text @click = "e1 = 2">
          Atras
        </v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
        
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'InspirePage',
  data () {
      return {
        e1: 1,
        picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      }
    },
}
</script>