<template>
  
  <div >

    <v-col cols="12" sm="10" >
          <v-row justify="center" align="center">
             <center>
          <v-form action="">
            <p class="ma-4 ms-12">
              Buscar Cédula: <input  v-mask="['#.###.###','##.###.###']" autocomplete="off" style="color:white; background:transparent;" method="post" type="search"  name="buscarcedula" placeholder="V-">
              <v-btn dark small color="gray">Buscar
              <v-icon dark>
                mdi-account-search
              </v-icon>
              </v-btn>
            </p>
          </v-form>
        </center>
        <a href="Javascript:window.open('RegistrarUs','','width=800, height=600');">
        <v-row class="ma-4 ms-12" justify="center" align="center">
         
           <v-btn class="sm=8" color="blue black--text">Registrar</v-btn>
        </v-row>
         
        </a>
          </v-row>
        
      </v-col>

    <v-data-table
      :headers="headers"
      :items="desserts"
      :page.sync="page"
      :items-per-page="itemsPerPage"
      hide-default-footer
      class="elevation-1"
      @page-count="pageCount = $event"
    ></v-data-table>
    <div class="text-center pt-2">
      <v-pagination
        v-model="page"
        :length="pageCount"
      ></v-pagination>
    </div>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        page: 1,
        pageCount: 0,
        itemsPerPage: 10,
        headers: [
          {
            text: 'Nombre y Apellido',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Cédula', value: 'calories' },
          { text: 'Teléfono', value: 'fat' },
          { text: 'Iron (%)', value: 'iron' },
          
        ],
      }
    },
    methods: {
      sendata(){
        this.$axios.get({ params: {

        }})
      }
    }
  }
</script>