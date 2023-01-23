<template>
     <v-layout row wrap>
     <v-app class="black">
   <v-form class="ma-12">
   <v-container>    
    <v-card justify="center" align="center" color="transparent">
      <img src="/logo.png" alt="Vuetify.js">
    </v-card>
     
    <v-card color="transparent" width="1000">
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12">
     
      <v-stepper
    v-model="e6"
    vertical
  >
    <v-stepper-step
      :complete="e6 > 1"
      step="1"
    >
      Seleccione Especialidad
    </v-stepper-step>

    <v-stepper-content step="1">
      <v-card color="grey lighten-1" class="mb-12" height="200px">
        <v-row justify="center" align="center">
          <v-col sm="3" class="ma-14">   
            <v-select 
            background-color="primary"
            :items="Esp"
            label="Especialidad"
            outlined
            ></v-select>
          </v-col>
        </v-row>   
    </v-card>
      <v-btn color="primary" @click="e6 = 2">
        Continue
      </v-btn>
    </v-stepper-content>

    <v-stepper-step
      :complete="e6 > 2"
      step="2"
    >
      Seleccione Médico
    </v-stepper-step>

    <v-stepper-content step="2">
      <v-card color="grey lighten-1" class="mb-12" height="200px">
        <v-row justify="center" align="center">
          <v-col sm="3" class="ma-14">   
            <v-select 
            background-color="primary"
            :items="Esp"
            label="Médico"
            outlined
            ></v-select>
          </v-col>
        </v-row>   
    </v-card>
      <v-btn color="primary" @click="e6 = 3">
        Continue
      </v-btn>
      <v-btn @click="e6 = 1">
        Atrás
      </v-btn>
    </v-stepper-content>

    <v-stepper-step
      :complete="e6 > 3"
      step="3"
    >
      Seleccione Fecha de Cita
    </v-stepper-step>

    

  
  </v-stepper>

  <!--
              <v-stepper-items>
      
                <v-stepper-content step="2">
                  <v-card
                    class="mb-12"
                    color="grey lighten-1"
                    height="250px">
                    <v-row justify="center" align="center">
                      <v-col cols="6" sm="3"> 
                        <v-form class="ma-6">
                          <v-select 
                            :items="itemsM"
                            label="Especialidad"
                            outlined
                          ></v-select>
                          <v-select
                            :items="itemsP"
                            filled
                            label="Medico"
                            class="text-md-center"
                          ></v-select>
                        </v-form>     
                      </v-col>
                    </v-row> 
                  </v-card>
                    <v-btn
                      color="primary"
                      @click="e1 = 3">
                        Continue
                    </v-btn>
                </v-stepper-content>

                <v-stepper-content step="3">
                  <v-card
                    class="mb-12"
                    color="grey lighten-1"
                    height="400px">
                    <v-form class="mt-4">
                      <v-row justify="center" align="center">
                        <v-col  sm="8">
                          <v-date-picker
                            v-model="picker"
                            locale="es" 
                            :allowed-dates="allowedDates" 
                            min="2022-10-15" 
                            max="2023-04-20"> 
                  
                          </v-date-picker>
                        </v-col>
                      </v-row>
                    </v-form>
                  </v-card>
                    <v-btn
                      color="primary"
                      @click="e1 = 1">
                      Confirmar
                    </v-btn>
                    <v-btn @click = "e1 = 2">
                      Atras
                    </v-btn>
                </v-stepper-content>
              </v-stepper-items>
     -->
      
    </v-col>
  </v-row> 
</v-card>
</v-container>
</v-form>
</v-app>


</v-layout>
</template>

<script>


export default {
  name: 'InspirePage',
  data () {
      return {
        e6: 1,
        e1: 2,
        picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      }
    },
}
</script>