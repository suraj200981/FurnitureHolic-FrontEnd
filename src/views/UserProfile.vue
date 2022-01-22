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
                        <img src="https://ununsplash.imgix.net/photo-1431578500526-4d9613015464?fit=crop&fm=jpg&h=300&q=75&w=400" alt="..."/>
                    </div>
                    <div class="card-body">
                        <div class="author">
                            <img class="avatar border-gray" src="" alt="..."/>
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
                  console.log(this.user);
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