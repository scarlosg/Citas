<template>
  <v-form>
    <v-container>
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
      <v-text-field v-mask="['#.###.###','##.###.###']" label="Numero de Cedula"></v-text-field>
    </v-col>
 
        <v-col
          cols="3"
          md="3"
        >
          <v-text-field
            v-model="Nacimiento"
            v-mask="['##/##/####']"
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
            :rules="nameRulesT"
             label="Telefono"
            required
          ></v-text-field>
        </v-col>
      </v-col>
      
      <v-radio-group v-model="radioGroup">
      <v-radio
        v-for="n in 3"
        :key="n"
        :rules="Genero"
        :label="`Femenino, Masculino, Otros  ${n}`"
        :value="n"
      ></v-radio>
    </v-radio-group>

      <v-col
      class="d-flex"
      cols="12"
      sm="3"
    >
        <v-select
          :items="itemsE"
          label="Estado"
          outlined
        ></v-select>
      </v-col>
      
        <v-col
        class="d-flex"
        cols="12"
        sm="3"
      >
        <v-select
          :items="itemsC"
          label="Ciudad"
        ></v-select>
      </v-col>

      <v-col
        class="d-flex"
        cols="12"
        sm="3"
      >
        <v-select
          :items="itemsM"
          label="Municipio"
          outlined
        ></v-select>
      </v-col>

      <v-col
        class="d-flex"
        cols="12"
        sm="3"
      >
        <v-select
          :items="itemsP"
          filled
          label="Parroquia"
        ></v-select>
      </v-col>

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
    items: ['Venezolano', 'Extranjero', 'Pasaporte',],
    itemsE: ['Amazonas','Anzoátegui','Apure','Aragua','Barinas','Bolívar','Carabobo','Cojedes','Delta Amacuro','Distrito Federal','Falcón','Guárico','Lara','Mérida','Miranda','Monagas','Nueva Esparta','Portuguesa','Sucre','Táchira','Trujillo','Vargas','Yaracuy','Zulia',],
    itemsC: ['Barquisimeto'],
    itemsP: ['Ana Soto'],
    itemsM: ['Iribarren'],

    nameRules: [
      v => !!v || 'Los Nombres son Requeridos',
      v => v.length <= 50 || 'Muy Largo',
    ],

    nameRulesA: [
    v => !!v || 'Los Apellidos son Requeridos',
      v => v.length <= 30 || 'Muy Largo',
    ],

    cedulaRules:[
      v => !!v || 'Cedula Requerida',
      v=> v.length <= 8 || 'Cedula no valida',
      v=> v,
    ],

    nameRulesD: [
    v => !!v || 'Dirección Requerida',
      v=> v.length >= 5 || 'Dirección no valida',
      
    ],

    email: '',
    emailRules: [
      v => !!v || 'E-mail es Requerido',
      v => /.+@.+/.test(v) || 'E-mail no es valido',
    ],
    nameRulesT: [
    v => !!v || 'Telefono Requerido',
    ],

    Genero: [

    ],

  }),
}
</script>