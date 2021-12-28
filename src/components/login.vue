<template>
  <v-container>
      <v-col cols="12">
        <v-img
          :src="require('../assets/White logo - no background.png')"
          class="my-3"
          contain
          height="500"
        />
      </v-col>

      <v-col style="margin-top:-50px">
        <h1 style="font-family: 'Pushster', cursive; color:#80D39B">
          Welcome to FurnitureHolic.com
        </h1>

        <p class="subheading font-weight-regular" style="color:#30321C">
          We are a leading online furniture store that offers a <br>wide variety of, 
          high quality, affordable furniture. You <br>sell or buy, its that simple. Please login below:
        </p>
      </v-col>
      <v-col>
       <center>
           <v-card flat style="width:70%;">

           <v-tabs   background-color="#80D39B"
      color="basil"
      grow
      style="height:500px!important;"
      dark
      icons-and-text>
      <v-tab>
        <v-icon>
          mdi-account
        </v-icon>
        Login
      </v-tab>
      <v-tab>
        <v-icon>
          mdi-account-plus-outline
        </v-icon>
        Register
      </v-tab>

      <v-tab-item>
        <v-card flat>
          <v-card-text>
            <v-form ref="form">
              <v-text-field
                v-model="login.Email"
                label="Email"
                type="email"
                prepend-icon="mdi-email"
                color="primary"
                :rules="emailRules"
                required
              ></v-text-field>

              <v-text-field
                v-model="login.Password"
                label="Password"
                type="password"
                prepend-icon="mdi-lock"
                color="primary"
                :rules="passwordRules"
                required
              ></v-text-field>
              <v-btn
                color="primary"
                block
                @click="loginPost"
               >
                Login</v-btn>
                <v-btn
                color="red"
                block style="color:white;margin-top:5px;">
               forgot password</v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-text>
           <!--register-->
           <v-form @submit="regPost" method="post">
             <v-text-field
              v-model="reg.Name"
              label="Name"
              type="text"
              prepend-icon="mdi-account"
              color="primary"
              :rules="nameRules"
              required

              ></v-text-field>
              <v-text-field
              v-model="reg.Email"
              label="Email"
              type="email"
              prepend-icon="mdi-email"
              color="primary"
              :rules="emailRules"
              required
              ></v-text-field>
              <v-text-field
              v-model="reg.Password"
              label="Password"
              type="password"
              prepend-icon="mdi-lock"
              color="primary"
              :rules="passwordRules"
              required
              ></v-text-field>
              <v-text-field
              v-model="confirmPassword"
              label="Confirm Password"
              type="password"
              prepend-icon="mdi-lock"
              color="primary"
              :rules="confirmPasswordRules"
              required 
              ></v-text-field>
              <v-text-field
              v-model="reg.Phone"
              label="Phone"
              type="text"
              prepend-icon="mdi-phone"
              color="primary"
              :rules="phoneRules"
              required
              ></v-text-field>
               <v-btn
                color="primary"
                block
                type="submit"
                @click="regPost"
               >
                Create account</v-btn>
              
           </v-form>

          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
           </v-card>
          </center>

      </v-col>
    
  </v-container>
</template>

<script>


import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import VueCookies from 'vue-cookies'

Vue.use(VueAxios, axios);
Vue.use(VueCookies);

  export default {
    name: 'login',

    data: () => ({
      jwt:{
        token:''
      },
      reg:{
        Name:null,
        Email:null,
        Password:null,
        Phone:null
      },
      login:{
        Email:null,
        Password:null
      },
      phoneRules: [
        v => !!v || 'Phone is required',
        v => v.length >= 10 || 'Phone must be at least 10 characters'
      ],
      nameRules: [
        v => !!v || 'Name is required',
        v => v.length >= 3 || 'Name must be at least 3 characters'
      ]
    }),

    methods: {
      //register
      regPost(e) {
        this.axios.post(
          'https://localhost:44316/api/users/register/',
          this.reg).then(response => {
          console.warn(response.data);

          if(response.status == 201){
            alert("Registration Successful");
            this.$router.push('/login');
          }
          
        }).catch(error => {
              alert("Registration Failed");
              console.log(error);
        });
        e.preventDefault(); 
      },
      //login
      loginPost(e){
        this.axios.post('https://localhost:44316/api/users/login/',this.login).then(response => {
        
                    console.warn(response.data);

        //stores token in cookie
        document.cookie = "jwt="+response.data.access_token+"; expires="+this.toDateTime(response.data.expiration_Time);
            
            alert("Login Successful");
            this.$router.push('/about');
          
        }).catch(error => {

          alert("Login Failed");
          console.log(error);
        });
        e.preventDefault(); 
      },
       toDateTime(secs) {
    var t = new Date(1970, 0, 1); // Epoch
    t.setSeconds(secs);
    return t;
}
    }
  }
</script>
