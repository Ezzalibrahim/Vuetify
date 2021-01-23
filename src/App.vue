<template>
  <v-app>
  <v-app-bar app color="info" >
    <v-toolbar-title> DoctorIno</v-toolbar-title> 
    <v-spacer></v-spacer>
    <v-btn text rounded>Home</v-btn> 
    <v-btn text rounded>Login</v-btn> 
    <v-btn text rounded>Register</v-btn> 
  </v-app-bar>

    <!-- Login Form  -->
    <v-content>
      <v-card width="400" class="mx-auto mt-5">
        <v-card-title >
          <h1 class="display-1">Login Form </h1>
        </v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field label="Username" prepend-icon="mdi-account-circle"></v-text-field>
            <v-text-field label="Password" :type="showtype" @click:append="ChangeType" prepend-icon="mdi-lock" :append-icon="toggelIcon"></v-text-field>
          </v-form>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-btn color="info">Register</v-btn>
          <v-spacer></v-spacer>
          <v-btn color="deep-primary accent-4">Login</v-btn>
        </v-card-actions>
      </v-card>
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
          :key="link"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link }}
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
// import HelloWorld from './components/HelloWorld';
// import NavBar from './components/NavBar'

export default {
  name: 'App',

  components: {
    // NavBar
  },
  data :()=>{
    return{
        showPassword : false,
        links:[
          "Home","Login","Register"
        ]
    }
  },
  computed:{
    showtype(){
      console.log('showPasswords')
      // return this.showPassword ? 'text':'password';
      if (this.showPassword) {
        return "text";
      } else {
        return "password";
      }
    },
    toggelIcon(){
      return this.showPassword ? 'mdi-eye':'mdi-eye-off';
    }
  },
  methods:{
    ChangeType(){
      console.log('Change type');
      console.log(this.showPassword);
      this.showPassword = !this.showPassword;
    }
  }
};
</script>

<style >
  .hhh{
    display: block;
  }
</style>
