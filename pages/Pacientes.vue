<!-- eslint-disable vue/valid-v-slot -->
<template>
  <v-layout row wrap>
    <v-flex>
      <v-app class="black">

  <div>

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
         
           <v-btn class="sm=8" color="gray">Registrar</v-btn>
        </v-row>
         
        </a>
          </v-row>
        
      </v-col>

      <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="pacientes"
    class="elevation-1"
  >
    <template #top>
      <v-toolbar
        flat
      >
        <v-toolbar-title>Pacientes</v-toolbar-title>
        <v-divider
          class="mx-4"
          inset
          vertical
        ></v-divider>
        <v-spacer></v-spacer>
        <v-dialog
          v-model="dialog"
          max-width="500px"
        >
          <template #activator="{ on, attrs }">
            <v-btn
              color="primary"
              dark
              class="mb-2"
              v-bind="attrs"
              v-on="on"
            >
              Registrar Pacientes
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">{{ formTitle }}</span>
            </v-card-title>

            <v-card-text>
              <v-container>
                <v-row>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.name"
                      label="Nombre"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.lastname"
                      label="Apellido"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="6" md="2">
                  <v-select
                  :items="items"
                    label="Tipo"
                  ></v-select>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.cedula"
                      label="Cédula"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.fecha"
                      label="Fecha de Nacimiento"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.email"
                      label="E-mail"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.direccion"
                      label="Dirección"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.telefono"
                      label="Teléfono"
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-select
                     v-model="editedItem.genero"
                     :items="itemsG"
                      label="Genero"
                    >
                    </v-select>
                  </v-col>
                  <v-col
                    cols="6"
                    sm="3"
                    md="4"
                  >
                  <v-select 
                  :items="itemsM"
                  label="Municipio">
                  </v-select>
                </v-col>
                <v-col
                    cols="6"
                    sm="3"
                    md="4"
                  >
                  <v-select 
                  :items="itemsP"
                  label="Parroquia">
                  </v-select>
                </v-col>
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="blue darken-1"
                text
                @click="close"
              >
                Cancel
              </v-btn>
              <v-btn
                color="blue darken-1"
                text
                @click="save"
              >
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-dialog v-model="dialogDelete" max-width="500px">
          <v-card>
            <v-card-title class="text-h5">Are you sure you want to delete this item?</v-card-title>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="closeDelete">Cancel</v-btn>
              <v-btn color="blue darken-1" text @click="deleteItemConfirm">OK</v-btn>
              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>
    // eslint-disable-next-line vue/valid-v-slot
    <template #item.actions="{ item }">
      <v-icon
        small
        class="mr-2"
        @click="editItem(item)"
      >
        mdi-pencil
      </v-icon>
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
    </template>
    <template #no-data>
      <v-btn
        color="primary"
        @click="initialize"
      >
        Reset
      </v-btn>
    </template>
  </v-data-table>


   
  </div>
</v-app>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  data: () => ({
    dialog: false,
    dialogDelete: false,
    itemsM: ['[Seleccione]'],
    itemsP: ['[Seleccione]'],
    items:  ['V', 'E', 'P'],
    especialidad: ['Oftanmologia'],
    itemsG: ['Femenino', 'Masculino', 'Otros'],
    headers: [
      {
        text: 'Nombre y Apellido',
        align: 'start',
        sortable: false,
        value: 'name',
      },
      { text: 'Cédula', value: 'cedula' },
      { text: 'Fecha', value: 'fecha' },
      { text: 'Dirección', value: 'direccion' },
      { text: 'Teléfono', value: 'telefono' },
      { text: 'Genero', value: 'genero' },
      { text: 'Municipio', value: 'municipio' },
      { text: 'Parroquia', value: 'parroquia'},
      { text: 'Actions', value: 'actions', sortable: false },
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      name: '',
      tipo: '',
      cedula: '',
      fecha: '',
      email: '',
      telefono: '',
      genero: '',
      municipio: '',
      parroquia: '',
    },
    defaultItem: {
      name: '',
      tipo: '',
      cedula: '',
      fecha: '',
      email: '',
      telefono: '',
      genero: '',
      municipio: '',
      parroquia: '',
    },
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'Registro de Pacientes' : 'Editar'
    },
  },

  watch: {
    dialog (val) {
      val || this.close()
    },
    dialogDelete (val) {
      val || this.closeDelete()
    },
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.desserts = [
        {
          name: 'Frozen Yogurt',
          cedula: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
        },
      ]
    },

    editItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialogDelete = true
    },

    deleteItemConfirm () {
      this.desserts.splice(this.editedIndex, 1)
      this.closeDelete()
    },

    close () {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    closeDelete () {
      this.dialogDelete = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.desserts[this.editedIndex], this.editedItem)
      } else {
        this.desserts.push(this.editedItem)
      }
      this.close()
    },
  },
}
</script>