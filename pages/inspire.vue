<template>
  <v-form>
    <v-container>
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
      <v-row>
        <v-col
          cols="20"
          md="3"
        >
          <v-text-field 
            v-model="firstname"
            :rules="nameRules"
            :counter="50"
            label="Nombres"
            required           
          ></v-text-field>
        </v-col>

        <v-col
          cols="10"
          md="3"
        >
          <v-text-field
            v-model="lastname"
            :rules="nameRulesA"
            :counter="30"
            label="Apellidos"
            required
          ></v-text-field>
        </v-col>

        
    <v-col cols="6" md="3">
      <v-select
        :items="items"
        label="Cedula"
      ></v-select>
      <v-text-field v-mask="['#.###.###','##.###.###']" placeholder="V-" label="Numero de Cédula"></v-text-field>
    </v-col>
 
        <v-col
          cols="3"
          md="3"
        >
          <v-text-field
            v-model="Nacimiento"
            v-mask="['##/##/####']"
            placeholder="DD/MM/AAAA"
            :rules="nameRulesFe"
            label="Fecha de Nacimiento"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="10"
          md="3"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            placeholder="ejemplo@ejemplo.com"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="10"
          md="3"
        >
          <v-text-field
            v-model="direccion"
            :rules="nameRulesD"
            :counter="100" 
             label="Dirección"
            required
          ></v-text-field>
        </v-col>
        
        <v-col
        class="d-flex"
        cols="12"
        sm="3"
      >
      <v-col
          cols="3"
          md="10"
        >
          <v-text-field
            v-model="Telefono"
            v-mask="['####-###-####']"
            placeholder="04XX-000-0000"
            :rules="nameRulesT"
             label="Telefono"
            required
          ></v-text-field>
        </v-col>
      </v-col>
      
      <p>Genero</p>
    <v-radio-group
      v-model="radios"
      mandatory
    >
      <v-radio
        label="Femenino"
        value="radio-1"
      ></v-radio>
      <v-radio
        label="Masculino"
        value="radio-2"
      ></v-radio>
      <v-radio 
      label ="Otro"
      value="radio-3"
      ></v-radio>
    </v-radio-group>

    <v-bottom-navigation
        :value="value"
        color="teal"
        grow>

    <v-btn>
      <span>Registrar</span>
      <v-icon>mdi-account-plus</v-icon>
    </v-btn>

    <v-btn>
      <span>Editar</span>
      <v-icon>mdi-account-edit</v-icon>
    </v-btn>
  </v-bottom-navigation>

      </v-row>    
    </v-container>
  </v-form>
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
      v=> v.length <= 8 || 'Cédula no valida',
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
      v => !!v || 'Telefono Requerido',
      
    ],

    nameRuleFe: [
      v => !!v || 'Fecha Requerido',
    ],

  }),
}
</script>