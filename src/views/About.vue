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
    <h1 position="absolute">This will be the page after login</h1>
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
        Authorization: 'Bearer ' + this.$store.state.jwt.token
      }
    }).then(response => {
      console.warn(response.data);
    }
    ).catch(error => {
      console.warn(error);
    });
  }
})
</script>
