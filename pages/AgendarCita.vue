<template>
  <v-row>
    <v-col class="text-center">
      <img src="/logo.png" alt="Vuetify.js" class="mb-5" />
      
      <center>
      <v-form action="">
        <p>
          Buscar Cédula: <input v-mask="['#.###.###','##.###.###']" type="search"  name="buscarcedula" placeholder="V-">
          <v-btn dark small color="gray">Buscar
            <v-icon dark>
        mdi-account-search
        </v-icon>
          </v-btn>
        </p>
      </v-form>

          <footer>
            <small>
              <em>&mdash;Carlos</em>
            </small>
          </footer>

      <v-col
        class="d-flex"
        cols="12"
        sm="4"
      >
        <v-select
          :items="nameEspecialidad"
          label="Especialidad"
          dense
        ></v-select>
      </v-col>

      <v-col
        class="d-flex"
        cols="12"
        sm="4"
      >
        <v-select
          :items="nameMedico"
          label="Médico"
          dense
        ></v-select>
      </v-col>
      </center>

    </v-col>
   
  </v-row>
  
</template>

<script>
export default {
  name: 'InspirePage',
}
</script>