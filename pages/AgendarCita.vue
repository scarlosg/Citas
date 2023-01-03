<template>
    <v-form>
      <v-parallax dark src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg" height="800" width="400">
      
   <v-container fluid>
  <v-row justify="center" align="center"> 
    <v-col class="text-center">
      <v-row  justify="center" align="center">
      <v-card height="150px" width="150px" color="light-blue lighten-3">
        <img src="/logo.png" alt="Vuetify.js">
      </v-card>
      </v-row>
        <v-stepper v-model="e1">
            <v-stepper-header>
              <v-stepper-step
                :complete="e1 > 1"
                step="1">
                Buscar Cédula
              </v-stepper-step>

                  <v-divider></v-divider>

              <v-stepper-step
                :complete="e1 > 2"
                step="2">
                Especialidad y Medico
              </v-stepper-step>

                  <v-divider></v-divider>

              <v-stepper-step step="3">
                Fecha de Cita
              </v-stepper-step>
            </v-stepper-header>

              <v-stepper-items>
                <v-stepper-content step="1">
                  <v-card
                    class="mb-12"
                    color="grey lighten-1"
                    height="250px">

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
                      @click="e1 = 2">
                        Siguiente
                    </v-btn>
                </v-stepper-content>

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
                    <v-btn @click="e1 = 1">
                      Atras
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
        </v-stepper>
    </v-col>
  </v-row> 
</v-container>
></v-parallax>
 </v-form>

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
    methods: {
      allowedDates: val => ![6, 5].includes(new Date(val).getDay()),
    },
}
</script>