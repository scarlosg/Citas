<template>
  
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      color="indigo lighten-2">
      <v-list>
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
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-toolbar-title>{{ title }}</v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
   
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
          icon: 'mdi-account-edit-outline',
          title: 'Registrar Paciente',
          to: '/RegistrarUs',
        },
        
        {
          icon: 'mdi-doctor',
          title: 'Registrar Medico',
          to: '/Inspire',
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
        {
          icon:"",
          title:"Pacientes",
          to:"/Pacientes",
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
