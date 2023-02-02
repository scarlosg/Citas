
<template>
  
  <v-app>
   
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      width="200px"
      color="deep-orange lighten-3">
      <v-list>
        <v-card color="transparent" align="center" flat height="100px">
          <img src="/logo (2).png" alt="Vuetify.js" class="mb-6" height="90px" width="90px"/>
        </v-card>

        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    
    <v-app-bar :clipped-left="clipped" fixed app>  
      <v-row justify="center" align="center" class="ms-16">
         <v-toolbar-title>{{ title }}</v-toolbar-title>
      </v-row>  
     
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
  
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-home",
          title: 'Inicio',
          to: '/',
        },
        {
          icon:"mdi-account-injury",
          title:"Pacientes",
          to:"/Pacientes",
        },
        {
          icon:"mdi-doctor",
          title: "Medicos",
          to: "/Medicos"
        },
        {
          icon:" mdi-calendar-range",
          title:"Agendar Cita",
          to:"/AgendarCita",
        },
        {
          icon:" mdi-chart-bar-stacked",
          title:"Reporte",
          to:"/Reporte",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Instituto Municipal para el Desarrollo Social - Iribarren',
    }
    
  },
  
}

</script>
