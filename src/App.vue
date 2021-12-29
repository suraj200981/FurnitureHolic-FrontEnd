<template>
  <div>

    <v-app>
    <v-app-bar
      absolute
      color="#80D39B"
    >
      <template v-slot:extension>
        <v-tabs align-with-title>
         <router-link to="/login" style="color:white; text-decoration:none;"> <v-tab> login</v-tab></router-link>
         <router-link to="/productspage" style="color:white; text-decoration:none;"> <v-tab> Products</v-tab></router-link>
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
    <!-- -->
  </v-footer>
</v-app>
  </div>
</template>

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
