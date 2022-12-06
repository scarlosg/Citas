<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
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
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="lastname"
            :rules="nameRules"
            :counter="30"
            label="Apellidos"
            required
          ></v-text-field>
        </v-col>

        <v-row align="center">
    <v-col cols="12">
      <v-select
        :items="items"
        
        label="Cedula"
      ></v-select>
      <v-text-field label="Numero de Cedula"></v-text-field>
    </v-col>
  </v-row>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
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
    items: ['Venezolano', 'Extranjero', 'Pasaporte',],
    nameRules: [
      v => !!v || 'Los Nombres son Requeridos',
      v => v.length <= 50 || 'Muy Largo',
    ],
    cedula: '',
    cedulaRules:[
      v => !!v || 'Cedula Requerida',
      v=> v.length <= 8 || 'Cedula no valida',
      v=> v,
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail es Requerido',
      v => /.+@.+/.test(v) || 'E-mail no es valido',
    ],
  }),
}
</script>