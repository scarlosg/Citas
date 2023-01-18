<template>
    <v-row>
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
      methods: {
        allowedDates: val => ![6, 5].includes(new Date(val).getDay()),
      },
  }
  </script>