<template>
<div>
  <!----user profile -->
    <div class="container" style="margin: auto!important;
    margin-left: auto!important;
    margin-right: auto!important;
    display: block;
    width: 20%;">
        <div class="row">
        <div class="col-md-12">
            <div class="card">
            <div class="card-header">
                <h4 class="card-title"> User Profile </h4>
            </div>
            <div class="card-body">
                <div class="row">
                <div class="col-md-3">
                    <div class="card card-user">
                    <div class="image">
                    </div>
                    <div class="card-body">
                        <div class="author">
                             <img style="border-radius: 50%; height:300px; padding-top:100px" v-bind:src="userDP" alt="..."/>
                            <h5 class="title" style="text-align:center;">Mr {{user.name}}</h5>
                        <p class="description">
                            Email: {{userEmail}}
                            <br>
                            Phone: {{user.phone}}
                        </p>
                        </div>
                    </div>
                    </div>
                </div>
                </div>
            </div>
            </div>
        </div>
        </div>
    </div>
         
</div>
</template>


<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import VueCookies from 'vue-cookies'

Vue.use(VueAxios, axios);
Vue.use(VueCookies);

export default ({
  name: 'UserProfile',
 data: () => ({
      user : [],
      userEmail: '',
      userDP:'',
    }),

  beforeMount(){
 //check if the token from cookie is valid else redirect to login page
    this.axios.get('https://localhost:44316/api/users/AuthenticateUser',{
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      }
    }).then(response => {
      if(response.status == 200){
            console.log("Authenticated");
         //  console.warn(response.data);

     this.axios.get('https://localhost:44316/api/users/GetUserInformation',{ 
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      },
      params: { email: this.$cookies.get('user') } }).then(res => {
          this.user = res.data[0];
          this.userEmail = this.$cookies.get('user');

          this.userDP = 'https://localhost:44316/' + this.user.imageUrl;

      }).catch(err => {
        console.log(err);
      });
      }
    }).catch(error => {
            console.warn(error);
            location.href = 'http://localhost:8080/pagenotfound';

    });
  }
})
</script>