<!-- eslint-disable vue/valid-v-slot -->
<template>
  <v-layout row wrap>
    <v-flex>
      <v-app class="black">

  <div>

    

      <v-card color="transparent" class="ma-8">
    <v-row justify="center" align="center">
      <v-col
                    cols="6"
                    sm="6"
                    md="4"
                  >
              <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Buscar"
                single-line
                hide-details
              ></v-text-field>
            </v-col>
    </v-row>
            
      </v-card>
      <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="citas"
    class="elevation-1"
    :search="search"
  >
    <template #top>
      <v-toolbar
        flat
      >
        <v-toolbar-title>Citas</v-toolbar-title>
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
              Agendar Cita
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">{{ formTitle }}</span>
            </v-card-title>

            <v-card-text>
              <v-container>
                
         <v-row justify="center">
           <v-col
                    cols="12"
                    sm="12"
                    md="8"
                  >
                  <v-text-field
                  append-icon="mdi-magnify"
                  label="Buscar"
                  single-line
                  hide-details>
                  </v-text-field>
                </v-col>
         </v-row>
                 
         
                <v-row>             
                
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.name"
                      label="Nombre"
                      disabled
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
                      disabled
                    ></v-text-field>
                  </v-col>
                  
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.cedula"
                      label="Cédula"
                      disabled
                    ></v-text-field>
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
    search: '',
    dialog: false,
    dialogDelete: false,
    itemsM: ['[Seleccione]'],
    itemsP: ['[Seleccione]'],
    items:  ['V', 'E', 'P'],
    itemsG: ['Femenino', 'Masculino', 'Otros'],
    headers: [
      {
        text: 'Nombres y Apellidos',
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
      { text: 'Parroquia', value: 'parroquia', sortable: false },
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
      return this.editedIndex === -1 ? 'Pacientes' : 'Editar'
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