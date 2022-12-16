<template>
  <v-row>
    <v-col class="text-center">
      <img src="/v.png" alt="Vuetify.js" class="mb-5" />
      
      <center>
      <v-col  md="2">
      <v-text-field v-mask="['#.###.###','##.###.###']" label="Cédula"></v-text-field> 
        <v-btn  dark small color="gray"> Buscar
        <v-icon dark color="red">
        mdi-account-search
        </v-icon>
        </v-btn>
        </v-col>
      </center>
          <footer>
            <small>
              <em>&mdash;Carlos</em>
            </small>
          </footer>
       
    </v-col>
   
  </v-row>
</template>

<script>
export default {
  name: 'InspirePage',
}
</script>