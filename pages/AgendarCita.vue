<template>
     <v-layout row wrap>
     <v-app class="blue accent-2">
   <v-form class="ma-12">
   <v-container>    
   
     
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
      <v-card color="deep-purple darken-4" class="mb-12" height="200px">
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
      <v-card color="deep-purple darken-4" class="mb-12" height="200px">
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

    <v-stepper-content step="3">
      <v-card color="deep-purple darken-4" class="mb-12" height="200px">
        <v-row justify="center" align="center">
    <v-col
      cols="12"
      sm="6"
      md="4"
      class="ma-14"
    >
      <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        :return-value.sync="date"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template #activator="{ on, attrs }">
          <v-text-field
            v-model="date"            
            label="Fecha"
            prepend-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on"
           
          ></v-text-field>
        </template>
        <v-date-picker
          v-model="date"
          no-title
          scrollable
          locale="es"
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.menu.save(date)"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
    </v-col>
   
  </v-row>
      </v-card>
      <v-btn color="primary">
        Confirmar
      </v-btn>
      <v-btn @click="e6 = 2">
        Atrás
      </v-btn>
    </v-stepper-content>
  
  </v-stepper>
      
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
        date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      menu: false,
      modal: false,
      menu2: false,
      }
    },
    methods: {
        allowedDates: val => ![6, 5].includes(new Date(val).getDay()),
      },
}
</script>