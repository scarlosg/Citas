<!-- eslint-disable vue/valid-v-slot -->
<template>
  <v-layout row wrap>
    <v-flex>
      <v-app class="red">

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
        <v-toolbar-title>Médicos</v-toolbar-title>
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
              Registrar Médicos
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
                      :rules="nameRules"
                      :counter="50"
                      label="Nombres"
                      required  
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.lastname"
                      label="Apellidos"
                      :rules="nameRulesA"
                      :counter="30"
                      required
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
                      v-mask="['#.###.###','##.###.###']"
                       :rules= "cedulaRules"
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
                      v-mask="['##-##-####']"
                     placeholder="DD/MM/AAAA"
                     :rules="nameRulesFe"
                      label="Fecha de Nacimiento"
                      required
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
                      :rules="emailRules"
                      placeholder="ejemplo@ejemplo.com"
                      required
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
                      :rules="nameRulesD"
                      :counter="100" 
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.telefonoF"
                      v-mask="['####-###-####']"
                      :rules="nameRulesT"
                      placeholder="02XX-000-0000"
                      label="Teléfono Fijo"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col
                    cols="12"
                    sm="6"
                    md="4"
                  >
                    <v-text-field
                      v-model="editedItem.telefonoC"
                      v-mask="['####-###-####']"
                      :rules="nameRulesT"
                      placeholder="04XX-000-0000"
                      label="Teléfono Cedular"
                      required
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
                  v-model="editedItem.municipio"
                  :items="itemsM"
                  label="Iribarren"
                  disabled>
                  </v-select>
                </v-col>
                <v-col
                    cols="6"
                    sm="3"
                    md="4">
                  <v-select 
                  v-model="editedItem.parroquia"
                  :items="itemsP"
                  label="Parroquia">
                  </v-select>
                </v-col>
                <v-col
                    cols="6"
                    sm="3"
                    md="4"
                  >
                  <v-select 
                  v-model="editedItem.especialidad"
                  :items="itemsE"
                  label="Especialidad">
                  </v-select>
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
                Cancelar
              </v-btn>
              <v-btn
                color="black"
                text
                @click="save"
              >
                Guardar
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
        @click="editItem(item)">
        
        mdi-pencil
      </v-icon>
      <v-icon
      small
      class="mr-2"
     @click="visualizeItem(item)"
      >
        mdi-eye-outline
      </v-icon>
    </template>
    <template #no-data>
      <v-btn
        color="black"
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
      { text: 'Especialidad', value: 'especialidad'},
      { text: 'Opciones', value: 'actions', sortable: false },
    ],
    desserts: [],
    editedIndex: 1,
    editedItem: {
      cedula: '',
      name: '',
      lastname: '',
      tipo: '',
      fecha: '',
      email: '',
      telefono: '',
      genero: '',
      municipio: '',
      parroquia: '',
      especialidad: '',
    },
    defaultItem: {
      cedula: '',
      name: '',
      lastname: '',
      tipo: '',
      fecha: '',
      email: '',
      telefono: '',
      genero: '',
      municipio: '',
      parroquia: '',
      especialidad: '',
    },
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
      v=> v.length >= 9 || 'Número de Cédula no valida',
    ],
    emailRules: [
      v => !!v || 'E-mail es Requerido',
      v => /.+@.+/.test(v) || 'E-mail no es valido',
    ],
    nameRuleFe: [
      v => !!v || 'Fecha Requerido',
      v=> v,
    ],  
  }),
  

  computed: {
    formTitle () {
      return this.editedIndex === 0 ? 'Médicos' : 'Editar' 
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
          cedula: '26540805',
          fecha: '01-05-1999',
          direccion: 'Las Americas',
          telefono: '0424-559-4094',
          genero: 'Masculino',
          municipio: 'Iribarren',
          parroquia: 'Ana Soto',
          especialidad: 'Oftanmología'
        },
      ]
    },

    visualizeItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
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