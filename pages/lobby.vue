<template>
  <div class="container">
    <div>
      <h1 class="font-titre">
        Lobby, Bonjour {{username}}
      </h1>
        <nuxt-link :to="{name: 'sensors'}" class="button--grey">
        Sensors
      </nuxt-link> 
        <nuxt-link :to="{name: 'alerts'}" class="button--grey">
        Alerts
      </nuxt-link> 
    </div>
  </div>
</template>

<script>
export default { 
  data() {
      return {     
        username: ""
      }
    },
    mounted() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404"
      this.token = localStorage.getItem("token") || this.$router.push('login');   
}
      }




</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
  'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
}
.links {
  padding-top: 15px;
}
</style>
