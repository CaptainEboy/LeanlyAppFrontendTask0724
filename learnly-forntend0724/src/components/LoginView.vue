<template>
    <form name="login-form" >
      <div class="mb-3">
        <label for="username">Email: </label>
        <input type="text" id="username" v-model="input.email" />
      </div>

      <div class="mb-3">
        <label for="password">Password: </label>
        <input type="password" id="password" v-model="input.password" />
      </div>

      <button class="btn btn-outline-dark" type="submit" v-on:click.prevent = "login()">
        Login
      </button>

      <p>Email is: {{input.email}}</p>
      <p>Password is: {{input.password}}</p>
    </form>

    <h3>Output: {{ this.output }}</h3>
</template>

<!-- <script>
export default {
name: 'LoginView',
}
</script> -->

<!-- <script>
export default {
  name: 'LoginView',

  data(){
    return{
        input:{
            email: "",
            password: ""
        }
    }
  }

}
</script> -->

<script>
import { SET_AUTHENTICATION, SET_USERNAME } from "../store/storeconstants";
export default {
  name: 'LoginView',
  data(){
    return{
        input:{
            email: "",
            password: ""
        },
        output: "",
    }
  },
  methods:{
    login(){
      //make sure email OR password are not empty
      if(this.input.email != "" || this.input.password != ""){
        this.output = "Authentication complete"
        // console.log("authenticated")
        //stores true to the set_authentication and username to the set_username 
        this.$store.commit(`auth/${SET_AUTHENTICATION}`, true);
        this.$store.commit(`auth/${SET_USERNAME}`, this.input.email);
        this.output = "Authentication complete."
      }else{
        console.log("Username and Password can not be empty")
      }
    }
  },
}
</script>