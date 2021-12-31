<template>
    <v-container>
        <v-card 
            width="40%" 
            class="mx-auto my-15 pa-10 login-card"
            >
            <v-card-title 
                class="justify-center">
                Login
            </v-card-title>
            <v-row>

                <v-text-field 
                    label="User Name"
                    outlined 
                    placeholder="User Name"
                    color="teal darken-4">

                </v-text-field>
            </v-row>
            <v-row>
                <v-text-field 
                    label="Password"
                    outlined 
                    placeholder="Password"
                    :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                    :type="showPassword ? 'text' : 'password'"
                    @click:append="showPassword = !showPassword"
                    color="teal darken-4">

                </v-text-field>
            </v-row>
            <v-row>
                <v-btn 
                    class="px-15 mx-auto" 
                    dark 
                    color="teal darken-4"
                    @click="login">
                    Login
                </v-btn>
            </v-row>
        </v-card>
    </v-container>
</template>


<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';

  
  @Component({
     components: {
        
      }
  })
  export default class Login extends Vue {
      private showPassword: any = false;
      private username: any = "";
      private password: any = "";
      
      login(){
          this.$store.dispatch("login");
      }

  }

  
</script>
<style scoped>
    .login-card{
        background-color: rgb(242, 253, 253);
    }
    
</style>