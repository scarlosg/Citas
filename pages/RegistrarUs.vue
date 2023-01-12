<template>
  <v-layout row wrap>
 
  <v-parallax 
  height="850"
  srcset="https://cdn.vuetifyjs.com/images/parallax/material.jpg">
  <v-form> 
     
    <v-container>
      
      <v-row justify="center" align="center">
        <v-col cols="12" sm="8" >
          <v-row justify="center" align="center">
             <center>
          <v-form action="">
            <p>
              Buscar Cédula: <input v-mask="['#.###.###','##.###.###']" method="post" type="search"  name="buscarcedula" placeholder="V-">
              <v-btn dark small color="gray">Buscar
              <v-icon dark>
                mdi-account-search
              </v-icon>
              </v-btn>
            </p>
          </v-form>
        </center>
      </v-row>
      </v-col>
      
      <v-card color="light-blue darken-4" width="1000px" >
    
      <v-row justify="center" align="center">

        <v-col cols="6" md="3">
          <v-text-field 
            v-model="firstname"
            :rules="nameRules"
            :counter="50"
            label="Nombres"
            required           
          ></v-text-field>
        </v-col>

        <v-col cols="6" md="3">
          <v-text-field 
            v-model="lastname"
            :rules="nameRulesA"
            :counter="30"
            label="Apellidos"
            required
          ></v-text-field>
        </v-col>

      </v-row>

      <v-row justify="center" align="center">

        <v-col cols="6" md="3">
          <v-select
           :items="items"
            label="Cédula"
          ></v-select>
          <v-text-field v-mask="['#.###.###','##.###.###']" label="Número de Cédula" placeholder="V-"></v-text-field>
        </v-col>  
 
        <v-col cols="3" md="3">
          <v-text-field
            v-model="Nacimiento"
            v-mask="['##/##/####']"
            placeholder="DD/MM/AAAA"
            :rules="nameRulesFe"
            label="Fecha de Nacimiento"
            required
          ></v-text-field>
        </v-col>

      </v-row>

      <v-row justify="center" align="center">
        <v-col cols="6" md="3">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            placeholder="ejemplo@ejemplo.com"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>

        <v-col cols="6" md="3">
          <v-text-field
            v-model="direccion"
            :rules="nameRulesD"
            :counter="100" 
            label="Dirección"
            required
          ></v-text-field>
        </v-col>
      </v-row>

      <v-row justify="center" align="center">

        <v-col cols="6" sm="5">
          <v-text-field
            v-model="Telefono"
            v-mask="['####-###-####']"
            :rules="nameRulesT"
            placeholder="04XX-000-0000"
             label="Teléfono"
            required
          ></v-text-field>
        </v-col>
    
        <v-col cols="6" sm="3">      
          <v-select 
            :items="itemsM"
            label="Municipio"
            outlined
          ></v-select>
        </v-col>
      </v-row>

      <v-row justify="center" align="center">
        <v-col cols="6" sm="3">      
          <v-select 
            :items="itemsM"
            label="Municipio"
            outlined
          ></v-select>
        </v-col>
        
        <v-col class="d-flex" cols="6" sm="3">
          <v-select
            :items="itemsP"
            filled
            label="Parroquia"
            class="text-md-center"
          ></v-select>
        </v-col>
      </v-row> 

    <v-bottom-navigation :value="value" grow>

      <v-btn>
        <span>Registrar</span>
        <v-icon>mdi-account-plus</v-icon>
      </v-btn>

      <v-btn>
        <span>Editar</span>
        <v-icon>mdi-account-edit</v-icon>
      </v-btn>
    </v-bottom-navigation>
    
   </v-card>
  </v-row>
    </v-container>
   
  </v-form>

   </v-parallax>
  
</v-layout>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    firstname: '',
    lastname: '',
    Cedula: '',
    direccion: '',
    Telefono: '',
    email: '',
    Nacimiento: '',
    items: ['Venezolano', 'Extranjero', 'Pasaporte'],
    itemsP: ['[Seleccione]'],
    itemsM: ['[Seleccione]'],

    nameRules: [
      v => !!v || 'Los Nombres son Requeridos',
      v => v.length <= 50 || 'Muy Largo',
    ],

    nameRulesA: [
    v => !!v || 'Los Apellidos son Requeridos',
      v => v.length <= 30 || 'Muy Largo',
    ],

    cedulaRules:[
      v => !!v || 'Cédula Requerida',
      v=> v.length <= 8 || 'Número de Cédula no valida',
      v=> v,
    ],

    nameRulesD: [
    v => !!v || 'Dirección Requerida',
      v=> v.length >= 5 || 'Dirección no valida',
      
    ],

    emailRules: [
      v => !!v || 'E-mail es Requerido',
      v => /.+@.+/.test(v) || 'E-mail no es valido',
    ],

    nameRulesT: [
      v => !!v || 'Teléfono Requerido',
      
    ],

    nameRuleFe: [
      v => !!v || 'Fecha Requerido',
    ],    
  })
}
</script>
