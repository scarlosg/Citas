<!-- eslint-disable vue/valid-v-slot -->
<template>
  <v-layout row wrap>
    <v-flex>
      <v-app class="white">

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
                color="deep-orange lighten-3"
                append-icon="mdi-magnify"
                label="Buscar"
                single-line
                hide-details
              ></v-text-field>
            </v-col>
    </v-row>
            
      </v-card>

      <v-card class="ma-10">

   
      <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="citas"
    class="elevation-1"
    color="black"
    :search="search"
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
              color="deep-orange lighten-3 black--text"
              class="mb-2"
              v-bind="attrs"
              v-on="on"
            >
              Registrar Paciente
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
                  
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="black"
                text
                @click="close"
              >
                Cancel
              </v-btn>
              <v-btn
                color="black"
                text
                @click="save"
              >
                Save
              </v-btn>
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
   </v-card>

   
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
    items:  ['V', 'E'],
    itemsG: ['Femenino', 'Masculino', 'Otros'],
    headers: [
      {
        text: 'Cédula',
        align: 'start',
        sortable: false,
        value: 'cedula',
      },
      { text: 'Nombres', value: 'name' },
      { text: 'Apellidos', value: 'lastname' },
      { text: 'Actions', value: 'actions', sortable: false },
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      name: '',
      lastname: '',
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
      lastname: '',
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
          name: 'Frozen',
          lastname: 'Yogurt',
          cedula: '11262360',
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