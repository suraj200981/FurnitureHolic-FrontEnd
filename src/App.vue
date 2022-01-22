<template>
  <div>

    <v-app>
    <v-app-bar
      absolute
      color="#80D39B"
    >
      <template v-slot:extension>
        <v-tabs align-with-title>
         <a href="/login" style="color:white; text-decoration:none;"> <v-tab> login</v-tab></a>
         <a href="/productspage" style="color:white; text-decoration:none;"> <v-tab> Products</v-tab></a>
         <v-spacer></v-spacer>
       <v-btn class="mx-2"  
              dark
              medium
              color="red"
              @click="logout()"><v-icon>mdi-logout</v-icon></v-btn>
        <v-btn class="mx-2"  
              dark
              medium
              color="indigo"
              @click="goToAccountPage()"
              ><v-icon>mdi-account</v-icon></v-btn>
        </v-tabs>
      </template>
    </v-app-bar>

  <!-- Sizes your content based upon application components -->
  <v-main>

    <!-- Provides the application the proper gutter -->
    <v-container fluid>
      
      <!-- If using vue-router -->
      <router-view/>
    </v-container>
  </v-main>

  <v-footer app>
  </v-footer>
</v-app>
  </div>
</template>
<script>

export default ({
  name: 'App',

  data:() => {
    return {
          signOut: false
    }
  },
  mounted() {
       this.axios.get('https://localhost:44316/api/users/AuthenticateUser',{
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      }
    }).then(response => {
      if(response.status == 200){
            console.log("Authenticated");
           console.warn(response.data);
           this.signOut = true;
      }
    }
    ).catch(error => {
      console.log("Token is not valid!");
      console.warn(error);
      this.signOut = true;
    });
  },
    methods: {
    logout(){
     this.$cookies.remove('jwt');
     this.$cookies.remove('user');
      location.href = 'http://localhost:8080/login';
    },
    goToAccountPage(){
      location.href = 'http://localhost:8080/userprofile';
    }
  }
})
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.v-window__container {
   
    height: 400px!important;
}

</style>
