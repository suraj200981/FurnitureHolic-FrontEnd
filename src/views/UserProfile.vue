<template>
<div>


<form method="post" enctype="multipart/form-data" style="padding-top:200px">
    <label for="fileToUpload">
  <div class="profile-pic" :style="{'background-image': 'url('+userDP+''+')'}">
      
      <span class="glyphicon glyphicon-camera"></span>
      <span>Change Image</span>
  </div>
  </label>
  <input type="File" name="fileToUpload" id="fileToUpload">
</form>
<div class="user-profile">
    <div v-if="!this.hideField" class="username">{{user.name}}</div>
    <v-text-field
    v-if="this.hideField"
    class="centered-input username"
            solo
            :placeholder="this.user.name"
            clearable
          ></v-text-field>
    <div>
         <v-text-field
    v-if="this.hideField"
    class="centered-input username"
            solo
            :placeholder="this.user.phone"
            clearable
          ></v-text-field>
            <v-text-field
    v-if="this.hideField"
    class="centered-input username"
            solo
            :placeholder="this.userEmail"
            clearable
          ></v-text-field>
          <v-textarea
            v-if="this.hideField"
          solo
          name="input-7-4"
          label="Solo textarea"
        ></v-textarea>
  <div v-if="!this.hideField" class="bio">Tel: {{user.phone}}</div>
    <div v-if="!this.hideField" class="bio">Email: {{userEmail}}</div>

    <div v-if="!this.hideField" class="description">Bio:
      I use to design websites and applications
      for the web.
    </div>
    </div>
  <ul class="data">
    <li>
      <span class="entypo-heart"> 127</span>
    </li>
    <li>
      <span class="entypo-eye"> 853</span>
    </li>
    <li>
      <span class="entypo-user"> 311</span>
    </li>
    <br>
    
    <v-btn v-if="!this.hideField" @click="edit()" color="primary"
>Edit</v-btn>
    <v-btn v-if="this.hideField" @click="hideEdit()" color="error">Hide</v-btn>
         <v-btn
      class="ma-2"
      :loading="loading2"
      :disabled="loading2"
      color="success"
      @click="uploadFile(), loader='loading2'"
    >
        Save Changes
      <template v-slot:loader>
        <span>Saving...</span>
      </template>
    </v-btn>
 </ul>
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
     Images:{
         selectedFile: null,
     },
      user : [],
      userEmail: '',
      userDP:'',
      hideField:false,
    }),

  beforeMount(){
 //check if the token from cookie is valid else redirect to login page
    this.axios.get('https://localhost:44316/api/users/AuthenticateUser',{
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      }
    }).then(response => {
      if(response.status == 200){
     this.axios.get('https://localhost:44316/api/users/GetUserInformation',{ 
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      },
      params: { email: this.$cookies.get('user') } }).then(res => {
          this.user = res.data[0];
          this.userEmail = this.$cookies.get('user');
          this.userDP = 'https://localhost:44316/' + this.user.imageUrl;
          this.userDP= this.userDP.replace('\\','');
        

      }).catch(err => {
        console.log(err);
      });
      }
    }).catch(error => {
            console.warn(error);
            location.href = 'http://localhost:8080/pagenotfound';

    });
  },
  methods:{
        uploadFile(){
            const formData = new FormData();
            const imagefile = document.querySelector('#fileToUpload');
            formData.append("Image", imagefile.files[0]);
            axios.put('https://localhost:44316/api/users/ChangeDisplayPicture/' +this.user.id, formData, {
                headers: {
                 Authorization: 'bearer ' + this.$cookies.get('jwt')
                }
            }).then(res => {
                console.log(res);
                location.href = 'http://localhost:8080/userprofile';

            }).catch(err => {
                console.log(err);
            });
        },
        edit(){
            if(this.hideField== false){
                this.hideField = true;
            }else{
                this.hideField = false;
            }
        },
        hideEdit(){
            this.hideField = false;
        },
      
       
  }


})
</script>

<style scoped>
/* CSS design by @jofpin */
@import url(https://fonts.googleapis.com/css?family=Raleway|Varela+Round|Coda);
@import url(http://weloveiconfonts.com/api/?family=entypo);

[class*="entypo-"]:before {
  font-family: 'entypo', sans-serif;
}
 .centered-input >>> input {
      text-align: center
    }
.text {
  color: white;
  font-size: 20px;
  position: absolute;
  top: 39%;
  left: 48%;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  text-align: center;
}

.container:hover .overlay {
  opacity: 1;
}


/* CSS design by @jofpin */
@import url(https://fonts.googleapis.com/css?family=Raleway|Varela+Round|Coda);
@import url(http://weloveiconfonts.com/api/?family=entypo);

[class*="entypo-"]:before {
  font-family: 'entypo', sans-serif;
}

body {
  background: #fffcdd;
  padding: 2.23em;
}

.title-pen {
  color: #333;
  font-family: "Coda", sans-serif;
  text-align: center;
}
.title-pen span {
  color: #55acee;
}

.user-profile {
  margin: auto;
	width: 25em; 
  height: 11em;
  background: #fff;
  border-radius: .3em;
}

.user-profile  .username {
  margin: auto;

  color: #658585;
  font-size: 1.53em;
  font-family: "Coda", sans-serif;
  font-weight: bold;
}
.user-profile  .bio {
  margin: auto;
  color: #e76043; 
  font-size: .87em;
  font-family: "varela round", sans-serif;
}
.user-profile > .description {
  margin: auto;
  margin-top: 1.35em;
  margin-right: 4.43em;
  width: 14em;
  color: #c0c5c5; 
  font-size: .87em;
  font-family: "varela round", sans-serif;
}
.user-profile > img.avatar {
	padding: .7em;
  margin-left: .3em;
  margin-top: .3em;
  height: 6.23em;
  width: 6.23em;
  border-radius: 18em;
}

.user-profile ul.data {
	margin: 2em auto;
	height: 3.70em;
  background: #4eb6b6;
  text-align: center;
  border-radius: 0 0 .3em .3em;
}
.user-profile li {
	margin: 0 auto;
  padding: 1.30em; 
  width: 33.33334%;
  display: table-cell;
  text-align: center;
}

.user-profile span {
	font-family: "varela round", sans-serif;
	color: #e3eeee;
  white-space: nowrap;
  font-size: 1.27em;
  font-weight: bold;
}
.user-profile span:hover {
  color: #daebea;
}

footer > h1 {
  display: block;
  text-align: center;
  clear: both;
  font-family: "Coda", sans-serif;
  color: #343f3d;
  line-height: 6;
  font-size: 1.6em;
}
footer > h1 a {
  text-decoration: none;
  color: #ea4c89;
}
.profile-pic {
    margin:auto ;
    border-radius: 50%;
    height: 150px;
    width: 150px;
    background-size: cover;
    background-position: center;
    background-blend-mode: multiply;
    vertical-align: middle;
    text-align: center;
    color: transparent;
    transition: all .3s ease;
    text-decoration: none;
    cursor: pointer;
    padding-top:60px!important;
}

.profile-pic:hover {
    background-color: rgba(0,0,0,.5);
    z-index: 10000;
    color: #fff;
    transition: all .3s ease;
    text-decoration: none;
}
form input[type="file"] {
          display: none;
          cursor: pointer;
 }


/*styling for save button */

.custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }

  /*End of styling for save button */


</style>