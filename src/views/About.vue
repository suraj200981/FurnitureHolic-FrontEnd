<template>
  <div>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <h1 position="absolute">Congratulations, you are an authenticated user! :)</h1> 
  </div>
</template>

<script>

export default ({
  name: 'About',
  data() {
    return {
      //
    }
  },
  mounted(){
    this.axios.get('https://localhost:44316/api/users/AuthenticateUser',{
      headers: {
        Authorization: 'bearer ' + this.$cookies.get('jwt')
      }
    }).then(response => {
      if(response.status == 200){
            console.log("Authenticated");
      console.warn(response.data);
      }
    }
    ).catch(error => {

      console.log("Token is not valid!");
      this.$router.push('/pagenotfound');
      console.warn(error);
    });
  }
})
</script>
