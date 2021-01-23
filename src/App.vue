<template>
  <v-app>
    <v-app-bar app color="info" >
      <v-toolbar-title> DoctorIno</v-toolbar-title> 
      <v-spacer></v-spacer>
      <v-btn 
        v-for="link in links"
        :key="link.label"
        text 
        rounded 
        :to="link.url" >
          {{ link.label }}
      </v-btn> 
      <!-- <v-btn text rounded to="/login" >Login</v-btn> 
      <v-btn text rounded >Register</v-btn>  -->
    </v-app-bar>
    <!-- Router element -->
    <v-content>
      <router-view></router-view>
    </v-content>
      <v-footer
        color="primary lighten-1"
        padless
      >
        <v-row
          justify="center"
          no-gutters
        >
          <v-btn
            v-for="link in links"
            :key="link.label"
            :to="link.url"
            color="white"
            text
            rounded
            class="my-2"
          >
            {{ link.label }}
          </v-btn>
          <v-col
            class="primary lighten-2 py-4 text-center white--text"
            cols="12"
          >
            {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
          </v-col>
        </v-row>
      </v-footer>
</v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
    // NavBar
  },
  data :()=>{
    return{
        links:[
          {
            label: "Home",
            url:"/"
          },{
            label: "Login",
            url:"/login"
          },{
            label: "Register",
            url:"/Register"
          },{
            label: "About Us",
            url:"/About"
          },{
            label: "Contact Us",
            url:"/Contact"  
          },
          {
            label:"Dashboard",
            url:"/Dashboard"
          }
        ]
    }
  },

};
</script>

<style >

</style>
