<template>
   <v-layout row wrap>
   <v-flex>
    <v-app class="blue accent-2">
    <div >
      <td>
        <span v-if="formActualizar && idActualizar == index">
          <button class="btn btn-success" @click="guardarActualizacion(index)" >Guardar</button>
        </span>
        <span v-else>

        </span>
      </td>
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
          <a href="Javascript:window.open('Inspire','','width=800, height=600');">
          <v-row class="ma-4 ms-12" justify="center" align="center">
             <v-btn class="sm=8" color="gray">Registrar</v-btn>
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
  </v-app>
  </v-flex>
</v-layout>
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